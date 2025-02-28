I will find the exact quotes from Vaswani et al. (2017) 'Attention Is All You Need' that explain the mathematical justification for scaling by \( \sqrt{d_k} \). This includes statements on how the unscaled dot-product grows in expectation with \( d_k \) and how scaling normalizes the variance of attention scores. I'll provide the exact lines from the paper shortly.

## Key Quotes from *Attention Is All You Need* (Vaswani et al., 2017) on Scaling by \( \sqrt{d_k} \)

- **Dot product grows with \(d_k\):** The authors point out that without scaling, larger key/query dimensions can inflate the dot-product magnitude, saturating the softmax. In Section 3.2.1, they write:  
  > *“We suspect that for large values of \(d_k\), the dot products grow large in magnitude, pushing the softmax function into regions where it has extremely small gradients.”* ([论文翻译——Attention Is All You Need - 小萝卜鸭 - 博客园](https://www.cnblogs.com/wwj99/p/12156301.html#:~:text=We%20suspect%20that%20for%20large,it%20has%20extremely%20small%20gradients))

- **Variance \(= d_k\) for independent components:** To explain this effect, they note that if each component of the query and key is an independent random variable (mean 0, variance 1), the dot product’s variance grows with the dimension. The paper illustrates:  
  > *“To illustrate why the dot products get large, assume that the components of \(q\) and \(k\) are independent random variables with mean 0 and variance 1. Then their dot product, \(q \cdot k = \sum_{i=1}^{d_k} q_i k_i\), has mean 0 and variance \(d_k\).”* ([论文翻译——Attention Is All You Need - 小萝卜鸭 - 博客园](https://www.cnblogs.com/wwj99/p/12156301.html#:~:text=To%20illustrate%20why%20the%20dot,0%20and%20variance%20d%20k))

- **Scaling stabilizes softmax:** To avoid extremely large dot-product values (and thus stabilize the softmax probabilities), the authors introduce the \(1/\sqrt{d_k}\) scaling factor. As the paper states:  
  > *“To counteract this effect, we scale the dot products by \(1/\sqrt{d_k}\).”*

Each of these quotes comes directly from Vaswani *et al.* (2017) and highlights that scaling by \( \sqrt{d_k} \) normalizes the expected variance of the dot product, preventing the softmax from operating in regions with vanishing gradients. This ensures more stable and effective attention computations.
