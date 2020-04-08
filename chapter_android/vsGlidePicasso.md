# Glide Picsasso Fresco 的对比

android的主流图片加载库 

## Picasson VS Glide 
两者很相似，有着近乎相同的API。
Glide在缓存策略和加载gif方面略胜一筹。

1. 使用方式相似，Glide不仅仅是context,还可以是Activity或者Fragment。
    和宿主生命周期保持一致。
2. Glide图片的加载质量要差于Picasso。
    Glide 默认bitmap格式为RGB_565比ARGB_8888的内存开销要小一般。
3. 缓存策略不一样。
    Glide 缓存和ImageView相同，所以加载速度快。
    Picasso 缓存全尺寸，在显示前重新调整大小。
4. Glide 可以加载gif。
5. Glide 约430k，方法数预约2678。
   Picasso 约118k，方法数量约480。
小结算：Picasso体积小图片质量高，加载稍慢。

## Fresco 
都能做。
1. 最大的优势在于5.0以下（最低2.3）的bitmap加载。5.0以下系统，Fresco将图片放在一个特别的内存区域，大大减少OOM。
2. 体积大。使用麻烦。
3. 适用于高质量加载大量图片。
