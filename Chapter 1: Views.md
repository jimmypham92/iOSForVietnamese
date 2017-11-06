# 1. Views
## 1. The Window

App được tạo ra thành nhiều tầng xếp chồng lên nhau. Tầng dưới cùng được gọi là window. Nó là một instance của đối tượng UIWindow, UIWindow là class con của UIView. Window sẽ được tạo ra ngay thời điểm khởi động ứng dụng. 

*Đồng nghĩa với việc, nếu ứng dụng cũng xuất ra những màn hình của thiết bị khác, tương ứng với số lượng màn hình là số lượng instance của UIWindow*

Quá trình tạo ra như sau: 
1. UIApplicationMain khởi tạo UIApplication, giữ nó lại để sử dụng. Bằng cách gọi tới UIApplication.shared. Sau đó khởi AppDelegate, bạn sẽ tạo appdelegate file và thêm @UIApplication vào. Sau đó sẽ gán appdelegate instance vào application delegate.

2. UIApplicationMain kiểm tra xem ứng dụng có sử dụng storyboard chính không bằng cách kiểm tra file Info.plist.

3. Nếu ứng dụng sử dụng storyboard. UIApplicationMain sẽ khởi tạo một instance của UIWindow và gán nó vào thuộc tính window của appdelegate. 

4. Nếu ứng dụng sử dụng storyboard, UIApplicationMain sẽ vào trong storyboard, khởi tạo initialViewController. Sau đó gán vào thuộc tính rootViewController của window.

5. UIApplication gọi tới application(_:didFinishLaunching- WithOptions:) của AppDelegate.

6. Giao diện của ứng dụng sẽ không được hiển thị khi window được trở thành key's window ( window chính ). Do đó nếu ứng dụng sử dụng storyboard, nó sẽ gọi tới hàm makeKeyAndVisible.

Khi ứng dụng đang hoạt động, có nhiều cách để gọi tới window:
- Nếu một UIView đang nằm trong giao diện, nó sẽ có tham chiếu tới UIWindow thông qua thuộc tính window.

    *Đây cũng là cách kiểm tra xem UIView có nằm trong interface hay không bằng cách check xem thuộc tính window có nil hay không*

- Thông qua thuộc tính window của App Delegate
- Thông qua thuộc tính keyWindow của UIApplication.shared. Đây không phải cách an toàn, vì trong một vài trường hợp, ví dụ như hiển thị alert, keyWindow sẽ khác.

