# Human-Activity-Recognition-LSTM
This project uses MATLAB to classify six human activities from mobile accelerometer data. LSTM and BiLSTM models were trained, with BiLSTM showing better overall performance.

In this project, I developed a complete LSTM-based classification pipeline for human activity recognition using MATLAB. The objective was to classify six physical activities—sitting, standing, lying, walking, walking upstairs, and walking downstairs—based on time-series accelerometer data collected from smartphones. The dataset consisted of triaxial acceleration readings recorded at 50 Hz from 30 individuals performing various activities.

I began by loading and visualizing the signal data from humanActivity.mat, focusing on the X-axis acceleration component for simplicity. For labeling, I used the Signal Labeler App, where I defined activity categories and annotated time segments with appropriate labels. After experimenting on a smaller segment, I imported the fully labeled dataset from labels.mat to proceed efficiently.

Next, I performed signal preprocessing using the Signal Analyzer App. I applied a high-pass filter with a 0.6 Hz cutoff to remove low-frequency drift and gravitational noise. I then divided the cleaned signal into overlapping windows of 128 samples each (50% overlap), resulting in over 10,000 signal segments. To align each segment with a single activity label, I used MATLAB’s framelbl function with mode-based consolidation, ensuring one dominant label per segment.

The labeled dataset was then split into training (80%), validation (10%), and testing (10%) subsets using splitlabels, preparing it for supervised learning. I constructed the initial LSTM architecture using the Deep Network Designer App, including a sequence input layer, a unidirectional LSTM layer (50 units), a fully connected layer, and classification layers. However, during experimentation, I found that performance plateaued for certain activity transitions.
![image](https://github.com/user-attachments/assets/941f80ad-0e03-433c-be07-e2db4fe96883)

To enhance classification accuracy, I replaced the unidirectional LSTM layer with a Bidirectional LSTM (BiLSTM) layer. The BiLSTM processes input sequences in both forward and backward directions, allowing the network to capture contextual information from both past and future time steps. This significantly improved the model’s ability to distinguish between activities with subtle or overlapping motion patterns, such as "walking upstairs" versus "walking downstairs".
![image](https://github.com/user-attachments/assets/372a1d26-9d7f-4f9f-a97d-cb16ecb5a004)

The network was trained using sequence-to-label classification, optimized through validation monitoring and mini-batch training. Evaluation on the test set confirmed the improved generalization achieved with BiLSTM, demonstrating superior precision and recall compared to the unidirectional model.
![image](https://github.com/user-attachments/assets/9c82368f-7971-4efe-b4ad-c00cf75cf66d)


In conclusion, I successfully implemented a robust BiLSTM-based signal classification framework in MATLAB. Leveraging tools like Signal Labeler, Signal Analyzer, and Deep Network Designer, I was able to streamline the entire workflow from data preprocessing to deep learning model deployment. The integration of BiLSTM notably boosted the recognition performance, validating its advantage in temporal pattern analysis for human activity recognition.
