---
layout: post
title: Matplotlib basic
category: Python
keywords: Matpoltlib
---

After install matplotlib, I learnt some basic uses to visualize data. I found that it is like matlab I learn indead. For basic,you can just adjust a lottle. For fancy one, you have to set numerous more specific settings. Here, I leave a collection of basic anlysis code, which was learnt from [morvanzhou](https://morvanzhou.github.io/).


## Line

```python
    import matplotlib.pyplot as plt
    import numpy as np
    
    x=np.linspace(-1,1,50)
    y=x+1
    
    plt.figure()
    plt.plot(x,y)
    plt.show()
```
    
## Two line with annotation


```python
    import matplotlib.pyplot as plt
    import numpy as np
    
    x=np.linspace(-50,50,500)
    y1=x
    y2=x**2
    
    plt.figure(num=2,figsize=(8,5))
    plt.plot(x,y1,color='red',linewidth=1,linestyle='--')
    plt.plot(x,y2,color='blue')
    plt.xlim((-50,50))
    plt.ylim((-50,50))
    plt.xlabel('I am X')
    plt.ylabel('I am Y')
    
    ax=plt.gca()
    ax.spines['right'].set_color('none')
    ax.spines['top'].set_color('none')
    
    ax.xaxis.set_ticks_position('bottom')
    ax.spines['bottom'].set_position(('data',0))
    
    ax.yaxis.set_ticks_position('left')
    ax.spines['left'].set_position(('data',0))
    
    # set line syles
    l1, = plt.plot(x, y1, label='linear line')
    l2, = plt.plot(x, y2, label='square line')
    plt.legend(loc='upper right')
    
    # plot
    x0 = 20
    y0 = x0
    plt.plot([x0, x0,], [0, y0,], 'k--', linewidth=2.5)
    # set dot styles
    plt.scatter([x0, ], [y0, ], s=50, color='b')
    
    # annotation
    plt.annotate(r'$x=%s$' % y0, xy=(x0, y0), xycoords='data', xytext=(+30, -30),
     textcoords='offset points', fontsize=16,
     arrowprops=dict(arrowstyle='->', connectionstyle="arc3,rad=.2"))
    
    plt.text(-37, 3, r'$This\ is\ the\ some\ text. \mu\ \sigma_i\ \alpha_t$',
     fontdict={'size': 16, 'color': 'r'})			 
    
    plt.show()
```   

## XYZ axis

```python
    import numpy as np
    import matplotlib.pyplot as plt
    from mpl_toolkits.mplot3d import Axes3D
    
    fig = plt.figure()
    ax = Axes3D(fig)
    
    # X, Y value
    X = np.arange(-4, 4, 0.25)
    Y = np.arange(-4, 4, 0.25)
    # grid like matlab
    X, Y = np.meshgrid(X, Y)
    R = np.sqrt(X ** 2 + Y ** 2)
    Z = np.sin(R)
    
    # plot 3d and contour
    ax.plot_surface(X, Y, Z, rstride=1, cstride=1, cmap=plt.get_cmap('rainbow'))
    ax.contourf(X, Y, Z, zdir='z', offset=-2, cmap=plt.get_cmap('rainbow'))
    # zlim
    ax.set_zlim(-2, 2)
    plt.show()
```
    
    
## Bar

```python
    import matplotlib.pyplot as plt
    import numpy as np
    
    n = 12
    X = np.arange(n)
    Y1 = (1 - X / float(n)) * np.random.uniform(0.5, 1.0, n) # upper
    Y2 = (1 - X / float(n)) * np.random.uniform(0.5, 1.0, n) # down
    
    plt.bar(X, +Y1)
    plt.bar(X, -Y2)
    
    plt.xlim(-0.5, n)
    plt.xticks(())
    plt.ylim(-1.25, 1.25)
    plt.yticks(())
    
    # color
    plt.bar(X, +Y1, facecolor='#9999ff', edgecolor='white')
    plt.bar(X, -Y2, facecolor='#ff9999', edgecolor='white')
    
    # number annotation
    for x, y in zip(X, Y1):
    # ha: horizontal alignment
    # va: vertical alignment
    plt.text(x, y, '%.2f' % y, ha='center', va='bottom')
    
    for x, y in zip(X, Y2):
    # ha: horizontal alignment
    # va: vertical alignment
    plt.text(x, -y, '%.2f' % y, ha='center', va='top')
        
    plt.show()
```    
    
## Contours

```python
    import matplotlib.pyplot as plt
    import numpy as np
    # the height function
    def f(x,y):
    return (1 - x / 2 + x**5 + y**3) * np.exp(-x**2 -y**2)
    
    n = 256
    x = np.linspace(-3, 3, n)
    y = np.linspace(-3, 3, n)
    X,Y = np.meshgrid(x, y)
    
    # use plt.contourf to filling contours
    # X, Y and value for (X,Y) point
    plt.contourf(X, Y, f(X, Y), 8, alpha=.75, cmap=plt.cm.hot)
    
    # use plt.contour to add contour lines
    C = plt.contour(X, Y, f(X, Y), 8, colors='black', linewidth=.5)
    
    plt.clabel(C, inline=True, fontsize=10)
    plt.xticks(())
    plt.yticks(())
```    
    
    
## Heatmap with colorbar

```python
    import matplotlib.pyplot as plt
    import numpy as np
    
    a = np.array([0.32, 0.34, 0.45,
      0.36, 0.44, 0.53,
      0.50, 0.55, 0.65]).reshape(3,3)
    plt.imshow(a, interpolation='nearest', cmap='bone', origin='lower')
    # colorbar
    plt.colorbar(shrink=.92)
    
    plt.xticks(())
    plt.yticks(())
    plt.show()
```

## Scatter

```python
    import matplotlib.pyplot as plt
    import numpy as np
    
    n = 1024# data size
    X = np.random.normal(0, 1, n) # 1024 of numbers between(0,1)
    Y = np.random.normal(0, 1, n)
    T = np.arctan2(X,Y) # for color value
    plt.scatter(X, Y, s=75, c=T, alpha=.5)
    plt.xlim(-1.5, 1.5)
    plt.xticks(())  # ignore xticks
    plt.ylim(-1.5, 1.5)
    plt.yticks(())  # ignore yticks
    plt.show()
```    
    
    
    
To be continue...