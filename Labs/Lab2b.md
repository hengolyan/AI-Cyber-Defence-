# Laboratory 2b — High-Load Cybersecurity with Morpheus Lite

## 1. Experiment Results

| Measure | Baseline | Normal | Burst | Sustained | Attack Surge |
|---|---:|---:|---:|---:|---:|
| Run ID | 408973dd-5fbf-4a1f-b365-41a9ebb9dc0e | f7751713-e2a9-48f1-b660-0595a5fd45ef | 682aeb4d-8083-4a6f-a5c0-9cd36ef2e3fa | 9d2196d0-f25e-4892-899a-4b04ff6ef539 | 0c56b40a-bbd4-4b66-9d3a-2eb037658944 |
| Generated events/s | 1.0 | 25.0 | 130.0 | 241.7 | 240.1 |
| Detector events/s | 1.0 | 21.4 | 19.4 | 19.8 | 22.0 |
| Orchestrator alerts/s | 1.0 | 21.4 | 19.3 | 19.8 | 21.9 |
| Detector utilization | 4.2% | 91.2% | 79.5% | 83.7% | 85.9% |
| Orchestrator utilization | 4.4% | 64.6% | 58.3% | 59.0% | 65.0% |
| Peak ingress backlog / capacity | 4 / 500 | 114 / 500 | 1447 / 500 | 4504 / 500 | 4757 / 500 |
| Peak alert backlog / capacity | 2 / 500 | 8 / 500 | 11 / 500 | 10 / 500 | 3 / 500 |
| Detector queue wait | 6.4 ms | 4572.5 ms | 26186.5 ms | 24834.0 ms | 54098.7 ms |
| Detector processing latency | 42.5 ms | 42.7 ms | 41.0 ms | 42.2 ms | 39.1 ms |
| Orchestrator queue wait | 9.5 ms | 4.3 ms | 4.8 ms | 4.5 ms | 4.4 ms |
| Orchestrator processing latency | 44.5 ms | 30.3 ms | 30.2 ms | 29.8 ms | 29.6 ms |
| Full-pipeline E2E latency | 95.3 ms | 4645.3 ms | 26253.0 ms | 24864.5 ms | 54130.5 ms |
| Final system status | NORMAL | OVERLOADED | OVERLOADED | OVERLOADED | OVERLOADED |
| Generated / Detected / Orchestrated | 120 / 120 / 120 | 500 / 500 / 500 | 1997 / 926 / 926 | 5000 / 743 / 742 | 4998 / 1109 / 1108 |

> Note: Peak backlog values were taken from the recorded metrics over the experiment, while the other displayed values correspond to the dashboard measurements captured during each run.

## 2. Bottleneck Identification

### Baseline
No significant bottleneck was observed during the baseline experiment. Generator, detector, and orchestrator throughput were aligned at approximately 1 event/s. Both queues remained almost empty, utilization was very low, and the final system status was NORMAL.

### Normal
The main bottleneck was the detector/ingress stage. The generator produced approximately 25 events/s while the detector processed about 21.4 events/s. This difference caused the ingress backlog to grow temporarily to approximately 114 events. Detector utilization reached 91.2%, and detector queue wait increased to 4572.5 ms. The alert queue remained very small, showing that the orchestrator was able to keep up with the detector output.

### Burst
The detector was clearly the bottleneck during burst load. The generator reached approximately 130 events/s on the dashboard and produced even higher short-term spikes, while the detector remained near 19.4 events/s. The ingress backlog peaked at approximately 1447 events. The detector queue wait reached 26186.5 ms, while detector processing time remained only 41.0 ms. This shows that most of the latency came from waiting in the queue rather than actual processing.

### Sustained High Load
The detector/ingress stage was again the main bottleneck. The generator maintained approximately 241.7 events/s while the detector processed only 19.8 events/s. As a result, the ingress backlog increased almost continuously and peaked at approximately 4504 events. The alert backlog remained very small, indicating that the orchestrator could process the alerts that reached it.

### Attack Surge
The primary bottleneck remained the detector/ingress stage. The generator produced approximately 240.1 events/s while the detector processed 22.0 events/s. The ingress backlog reached approximately 4757 events and detector queue wait rose to 54098.7 ms. The orchestrator was under more pressure than in the sustained experiment, with utilization increasing to 65.0%, but the alert backlog still remained close to zero. Therefore, the orchestrator did not become the first saturated stage in this run.

---

## 3. Reflection Questions

*1. Which stage saturated first, and what evidence supports your conclusion?*
The detector/ingress stage saturated first. In the higher-load experiments, the generator produced events much faster than the detector could process them. For example, during the sustained profile the generator produced 241.7 events/s while the detector processed only 19.8 events/s. This caused the ingress backlog to grow to more than 4,500 events. At the same time, the alert backlog remained very small, which shows that the orchestrator was generally able to keep up with the alerts that reached it.

*2. Did queue wait or processing time contribute more to total latency?* 
Queue wait contributed much more to the total latency. The detector processing time remained close to 40 ms in all experiments, while detector queue wait increased dramatically under load. For example, during the attack-surge experiment the detector queue wait reached 54,098.7 ms, while detector processing latency was only 39.1 ms. Therefore, most of the delay came from events waiting in the queue rather than from the actual processing itself.

*3. Why can latency rise even when the machine is not at 100% CPU utilization?*
Latency can rise because the pipeline can be limited by one specific stage even when the whole machine still has available CPU resources. Events may wait in queues because a downstream component cannot process them as quickly as they arrive. Other factors such as I/O, Kafka consumption rates, concurrency limits, and configured stage capacity can also increase latency without requiring 100% CPU utilization.

*4. Why does the attack-surge profile stress the orchestrator more than a normal profile with the same event count?*
The attack-surge profile contains a higher proportion of suspicious events. This means that more events are forwarded for deeper downstream analysis instead of being filtered earlier. As a result, the orchestrator receives more work. In our results, orchestrator utilization reached 65.0% during the attack-surge profile, compared with 59.0% during the sustained profile.

*5. When is early filtering beneficial, and what security risk can overly aggressive filtering create?*
Early filtering is beneficial when it removes clearly benign events before they reach expensive downstream analysis. This reduces load, saves processing resources, and helps prevent unnecessary queue growth. However, filtering that is too aggressive creates a security risk because suspicious or malicious events may be incorrectly discarded before deeper analysis. This could cause real attacks to be missed.

*6. Is graceful degradation preferable to attempting full analysis of every event? Justify your answer.*
Yes. Under extreme load, graceful degradation is preferable because trying to fully analyze every event can cause very large backlogs and unacceptable latency. A better approach is to prioritize the most important or suspicious events while reducing less critical processing. This allows the system to continue providing useful security analysis instead of becoming completely overloaded.

*7. Which metric would you use to trigger backpressure, and why?*

I would use ingress backlog utilization as the main backpressure trigger. A growing ingress backlog is direct evidence that events are arriving faster than the detector can process them. It therefore provides an early indication of overload. Triggering backpressure when the backlog reaches a defined threshold could help slow, delay, or prioritize incoming work before latency becomes too high.
---

## 4. Main Conclusions

The results show a clear transition from stable processing during baseline load to severe queue accumulation under higher event rates. Across the Normal, Burst, Sustained, and Attack Surge profiles, the detector/ingress stage was the first and primary bottleneck.

The strongest evidence was:

- generator throughput consistently exceeding detector throughput;
- increasing ingress backlog;
- very large detector queue-wait times;
- relatively stable detector processing latency;
- very small alert backlog;
- orchestrator throughput remaining close to detector alert throughput.

Therefore, the major source of performance degradation was not the time required to analyze a single event, but the accumulation of events waiting before detector processing.
