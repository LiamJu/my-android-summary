# Android屏幕适配

1. 屏幕参数
   
   一块屏幕通常具有一下几个参数：
   
   - 屏幕大小：屏幕对角线的长度，通常使用“ **寸** “来度量，例如4.7寸手机等
   - 分辨类：手机屏幕的像素点个数，例如720x1280就是屏幕分辨类，指宽有720个像素点，高有1280个像素点
   - PPI：每英寸像素（Pixels Per Inch）又称DPI（Dots Per Inch）。是由对角线的像素点数除以屏幕的大小得到的。
   
2. 系统屏幕密度
   
   | 密度   | ldpi    | mdpi    | hdpi    | xhdpi    | xxhdpi    |
   | :--- | :------ | :------ | :------ | :------- | :-------- |
   | 密度值  | 120     | 160     | 240     | 320      | 480       |
   | 分辨类  | 240x320 | 320x480 | 480x800 | 720x1280 | 1080x1920 |
   
3. Launcher icons尺寸
   
   | 密度   | ldpi  | mdpi  | hdpi  | xhdpi   | xxhdpi  | Google Play |
   | :--- | :---- | :---- | :---- | :------ | :------ | :---------- |
   | 分辨类  | 48x48 | 72x72 | 96x96 | 144x144 | 192x192 | 512x512     |
   
4. Action bar, Dialog & Tab icons
   
   | 密度      | 尺寸                        |
   | ------- | ------------------------- |
   | mdpi    | 24x24 area in 32x32       |
   | hdpi    | 36 × 36 area in 48 × 48   |
   | xhdpi   | 48 × 48 area in 64 × 64   |
   | xxhdpi  | 72 × 72 area in 96 × 96   |
   | xxxhdpi | 96 × 96 area in 128 × 128 |
   
5. Notification icons
   
   | 密度      | 尺寸                      |
   | ------- | ----------------------- |
   | mdpi    | 22 × 22 area in 24 × 24 |
   | hdpi    | 33 × 33 area in 36 × 36 |
   | xhdpi   | 44 × 44 area in 48 × 48 |
   | xxhdpi  | 66 × 66 area in 72 × 72 |
   | xxxhdpi | 88 × 88 area in 96 × 96 |
