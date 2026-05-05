| Model                 | RSME   | $R^2$      | MAE    | Notes          |
| --------------------- | ------ | -------- | ------ | -------------- |
| Base Linear Regression       | 0.2653 | -0.0319 | 0.2049 | Using Pipeline |
| Boosted Decision Tree | 0.2481 | 0.0976   | 0.1935 | Using Pipeline |
| LightGBM              | 0.1958 | 0.4344   | 0.1366 | Using AutoML   |
| XGBoost               | 0.2066 | 0.3925   | 0.1442 | Using AutoML   |
| Decision Forest       | 0.2525 | 0.0653   | 0.1858 | Using Pipeline |

----

The results show that model performance improves substantially as we move from linear to tree‑based to gradient‑boosting methods. 
The base linear regression model performs the worst, with a negative $R^2$ indicating it fails to capture meaningful structure in the data.
Tree‑based models such as the boosted decision tree and decision forest offer moderate improvements by modeling nonlinear patterns,
but their errors remain relatively high. The best performance comes from gradient boosting. LightGBM achieves the lowest RMSE and MAE
and the highest $R^2$, making it the most accurate model. XGBoost performs similarly well but slightly below LightGBM. Overall, LightGBM 
is the strongest model for this prediction task, with boosting methods clearly outperforming the others. However, the results could be
improved and further experimentation in the pre-processing may improve model performance..
