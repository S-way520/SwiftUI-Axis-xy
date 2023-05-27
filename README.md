# SwiftUI-Axis-xy
Plane Rectangular Coordinate System / SwiftUI / swift playground
# The first part
![IMG_1213](https://github.com/S-way520/SwiftUI-Axis-xy/assets/95877651/a01099bd-07eb-452a-97f1-ea4c968cb39a)
# The second part
Code file 1
```swift
import SwiftUI
@main
struct MyApp: App {
    var body: some Scene {
        WindowGroup {
            AxisView()
        }
    }
}
```
Code file 2
```swift
import SwiftUI
struct AxisView: View {
    var body: some View {
        GeometryReader { geometry in
            ZStack {
                // X轴(X-Axis)
                Path { path in
                    path.move(to: CGPoint(x: 0, y: geometry.size.height / 2))
                    path.addLine(to: CGPoint(x: geometry.size.width, y: geometry.size.height / 2))
                }
                .stroke(Color.blue, lineWidth: 2)
                // X轴正方向刻度(X-Axis positive direction scale)
                let numXTickMarksPos = Int(geometry.size.width / 40) / 2
                ForEach(1...numXTickMarksPos, id: \.self) { index in
                    Path { path in
                        let xPos = CGFloat(index) * 40 + geometry.size.width / 2
                        path.move(to: CGPoint(x: xPos, y: geometry.size.height / 2 - 5))
                        path.addLine(to: CGPoint(x: xPos, y: geometry.size.height / 2))
                    }
                    .stroke(Color.red, lineWidth: 1)
                    
                    Text("\(index * 5)")
                        .position(x: CGFloat(index) * 40 + geometry.size.width / 2, y: geometry.size.height / 2 + 15)
                }
                // X轴负方向刻度(X-Axis negative direction scale)
                let numXTickMarksNeg = Int(geometry.size.width / 40) / 2
                ForEach(-numXTickMarksNeg...(-1), id: \.self) { index in
                    Path { path in
                        let xPos = CGFloat(index) * 40 + geometry.size.width / 2
                        path.move(to: CGPoint(x: xPos, y: geometry.size.height / 2 - 5))
                        path.addLine(to: CGPoint(x: xPos, y: geometry.size.height / 2))
                    }
                    .stroke(Color.red, lineWidth: 1)
                    
                    Text("\(index * 5)")
                        .position(x: CGFloat(index) * 40 + geometry.size.width / 2, y: geometry.size.height / 2 + 15)
                }
                
                // Y轴(Y-Axis)
                Path { path in
                    path.move(to: CGPoint(x: geometry.size.width / 2, y: 0))
                    path.addLine(to: CGPoint(x: geometry.size.width / 2, y: geometry.size.height))
                }
                .stroke(Color.blue, lineWidth: 2)
                // Y轴正方向刻度(Y-Axis positive direction scale)
                let numYTickMarksNeg = Int(geometry.size.height / 40) / 2
                ForEach(-numYTickMarksNeg...(-1), id: \.self) { index in
                    Path { path in
                        let yPos = CGFloat(index) * 40 + geometry.size.height / 2
                        path.move(to: CGPoint(x: geometry.size.width / 2 - 5, y: yPos))
                        path.addLine(to: CGPoint(x: geometry.size.width / 2, y: yPos))
                    }
                    .stroke(Color.red, lineWidth: 1)
                    Text("\(abs(index) * 5)")
                        .position(x: geometry.size.width / 2 + 20, y: CGFloat(index) * 40 + geometry.size.height / 2)
                }
                // Y轴负方向刻度(Y-Axis negative direction scale)
                let numYTickMarksPos = Int(geometry.size.height / 40) / 2
                ForEach(1...numYTickMarksPos, id: \.self) { index in
                    Path { path in
                        let yPos = CGFloat(index) * 40 + geometry.size.height / 2
                        path.move(to: CGPoint(x: geometry.size.width / 2 - 5, y: yPos))
                        path.addLine(to: CGPoint(x: geometry.size.width / 2, y: yPos))
                    }
                    .stroke(Color.red, lineWidth: 1)
                    Text("-\(index * 5)")
                        .position(x: geometry.size.width / 2 + 20, y: CGFloat(index) * 40 + geometry.size.height / 2)
                }
            }
        }
    }
}
```
