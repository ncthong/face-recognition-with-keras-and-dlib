# Nhận diện khuôn mặt người với keras và dlib
Trong ví dụ này, Keras được sử dụng để triển khai mô hình CNN lấy cảm hứng từ dự án [OpenFace](http://cmusatyalab.github.io/openface/). Mô hình này là một biến thể của kiến ​​trúc NN4 và được xác định là mô hình nn4.small2 trong dự án OpenFace. Việc đào tạo mô hình nhằm mục đích tìm hiểu việc nhúng một hình ảnh rằng khoảng cách L2 giữa tất cả các khuôn mặt có cùng bản sắc là nhỏ và khoảng cách giữa một cặp khuôn mặt từ các danh tính khác nhau là lớn. Bằng cách chọn ngưỡng phù hợp, mô hình có thể nhận diện khuôn mặt trong tập dữ liệu riêng. Lưu ý rằng mô hình này có thể chạy trên CPU.

<img src="https://github.com/ncthong/face-recognition-with-keras-and-dlib/blob/master/result/res1.JPG" width="270"/> <img src="https://github.com/ncthong/face-recognition-with-keras-and-dlib/blob/master/result/phap.JPG" width="270"/> <img src = "https://github.com/ncthong/face-recognition-with-keras-and-dlib/blob/master/result/thong.JPG" width="270"><img src = "https://github.com/ncthong/face-recognition-with-keras-and-dlib/blob/master/result/phapthong1.JPG" width="270">

# Pre-requisite
 ## Install needed packages
 - opencv 3.4.5, keras 2.2.4, dlib 19.4.0 (can use the wheel file for windows)
 - tqdm 4.31.1, pandas 0.23.4, scipy 1.2.0
 ## Pre-trained models
 - Download `shape_predictor_68_face_landmarks.dat` from [here](https://github.com/AKSHAYUBHAT/TensorFace/blob/master/openface/models/dlib/shape_predictor_68_face_landmarks.dat) and put it in the project folder.
 
# Implement
 ## Prepare images for training

- In the folder `image` there are folders containing images of people that we want to recognize. Each folder has 5 images of a person. If you want to have more people, just create folders and put images inside. It is recommended to have at least 5 images per person and the number of images of each person should be equal. 

- The images used for training should have only ONE face of the person.

- Image file must be in `.jpg` format. 

- Run `face_detect_and_save.py`. It will go through images in folders in the `image` and detect the face and save it (replace the full image).

 ## Training and testing
 - Run `main.py`. It will do following things: 
   - Initialize models.
   - Load images for training.
   - Start training and save `train.embs` as the output (for instant use without training later).
   - Plot a graph showing the difference in the distance between match and unmatch training images. The value of threshold can be chosen to separate match and unmatch faces. Modify the `threshold` in line 137 in `main.py`.
   ![alt-text](https://github.com/ncthong/face-recognition-with-keras-and-dlib/blob/master/result/graph.JPG)
   - Test with images in the `test_image` folder. You can make this part a separate .py file, just need to load the `train.embs`.
   - Images for testing can have multiple faces. Faces from people not in the training data will be shown as "unknown".
   
# Reference
- [Original Code](https://github.com/habom2310/face-recognition-with-keras-and-dlib/)
- [Deep face recognition with Keras, Dlib and OpenCV](https://krasserm.github.io/2018/02/07/deep-face-recognition/)
