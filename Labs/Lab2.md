**comparation of the two methods:**
| Measure | Isolation Forest | Autoencoder + Embeddings |
|----------|-----------------:|-------------------------:|
| Detected anomalies | 33 | 37 |
| Precision | 0.970 | 0.865 |
| Recall | 1.000 | 1.000 |
| F1 Score | 0.985 | 0.928 |
| False Positives | 1 | 5 |
| False Negatives | 0 | 0 |

**part 6- Quantitative comparation- explanation**
Overall, both models achieved very good results on this dataset, as they successfully detected all true attack events. However, the Isolation Forest performed better than the Autoencoder for several reasons. 
First, it produced fewer false positives, resulting in a higher precision score. This means that it generated fewer unnecessary alerts and was more accurate in distinguishing between normal and anomalous events.
Second, the Autoencoder is more sensitive to deviations from the learned normal behavior. As a result, it may classify records with only slight behavioral differences as anomalies, even when they are actually normal.
In contrast, the Isolation Forest focuses on identifying clearly isolated and extreme outliers rather than small deviations.
Finally, this dataset is synthetic, meaning that the attack events were intentionally generated as obvious anomalies. Such anomalies are particularly well suited for the Isolation Forest, which is designed to detect isolated outliers. The Autoencoder, on the other hand, learns normal behavioral patterns and may be more useful for detecting complex behavioral anomalies in larger or more realistic datasets, where attacks are not always represented by extreme feature values.
