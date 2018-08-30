

```python
%matplotlib inline
import matplotlib.pyplot as plt
import numpy as np
```

### Basic


```python
plt.title('title')
plt.xlabel('x axis')
plt.ylabel('y axis')
plt.plot([1, 3, 2, 4])
```




    [<matplotlib.lines.Line2D at 0x115f3c4a8>]




![png](Matplotlib_2_1.png)


### Define x and y


```python
x = range(6)
plt.plot(x, [i**2 for i in x])
```




    [<matplotlib.lines.Line2D at 0x11565b198>]




![png](Matplotlib_4_1.png)



```python
x = np.arange(0, 1, 0.01)
plt.plot(x, [i**2 for i in x])
```




    [<matplotlib.lines.Line2D at 0x115cc52b0>]




![png](Matplotlib_5_1.png)


### More Features
* color, linewidth, linestype
* xticks, latex
* legend
* grid
* save fig


```python
x = np.linspace(-np.pi, np.pi, 256)
sin_y = np.sin(x)
cos_y = np.cos(x)
plt.plot(x, sin_y, label='Sin', color='red', linewidth=3.0, linestyle=':')
plt.plot(x, cos_y, label='Cos', color='blue', linewidth=3.0, linestyle='-')
plt.xticks([-np.pi, -np.pi/2, 0, np.pi/2, np.pi],
          [r'$-\pi$', r'$-\pi/2$', r'$0$', r'$+\pi/2$', r'$+\pi$'])
plt.yticks([-1,0,1],
          [r'$-1$', r'$0$', r'$+1$'])
plt.legend()
plt.grid(True)
plt.savefig('myplot.png')
```


![png](Matplotlib_7_0.png)


### Axis


```python
x = np.arange(1, 5)
plt.plot(x, x * 1.5, x, x * 3.0, x, x / 2.0)
plt.grid(True)
plt.axis()
```




    (0.85, 4.15, -0.07500000000000007, 12.575)




![png](Matplotlib_9_1.png)


Zoom in by setting axis


```python
x = np.arange(1, 5)
plt.plot(x, x * 1.5, x, x * 3.0, x, x / 2.0)
plt.grid(True)
plt.axis([2, 4, 0, 10])
```




    [2, 4, 0, 10]




![png](Matplotlib_11_1.png)


Set x limit and y limit


```python
x = np.arange(1, 5)
plt.plot(x, x * 1.5, x, x * 3.0, x, x / 2.0)
plt.grid(True)
plt.axis([2, 4, 0, 10])
plt.xlim(0, 5)
plt.ylim(-1, 13)
```




    (-1, 13)




![png](Matplotlib_13_1.png)


### Subplot


```python
plt.subplot(2,1,1)
plt.plot([1,3,2,4])
plt.xlabel("this is x axis")
plt.ylabel("this is y axis")

plt.subplot(2,1,2)
x = np.linspace(-np.pi, np.pi, 256)
sin_y = np.sin(x)
cos_y = np.cos(x)
plt.plot(x, sin_y, label="Sin")
plt.plot(x, cos_y, label="cos")
plt.legend()
plt.xticks([-np.pi, -np.pi/2, 0, np.pi/2, np.pi],
          [r'$-\pi$', r'$-\pi/2$', r'$0$', r'$+\pi/2$', r'$+\pi$'])
plt.yticks([-1,0,1],
          [r'$-1$', r'$0$', r'$+1$'])
plt.show()
```


![png](Matplotlib_15_0.png)


#### Text


```python
plt.subplot(2,2,1)
plt.xticks([]), plt.yticks([])
plt.text(0.5,0.5, 'subplot(2,2,1)',ha='center',va='center',size=20,alpha=.5)

plt.subplot(2,2,2)
plt.xticks([]), plt.yticks([])
plt.text(0.5,0.5, 'subplot(2,2,2)',ha='center',va='center',size=20,alpha=.5)

plt.subplot(2,2,3)
plt.xticks([]), plt.yticks([])
plt.text(0.5,0.5, 'subplot(2,2,3)',ha='center',va='center',size=20,alpha=.5)

plt.subplot(2,2,4)
plt.xticks([]), plt.yticks([])
plt.text(0.5,0.5, 'subplot(2,2,4)',ha='center',va='center',size=20,alpha=.5)
```




    Text(0.5,0.5,'subplot(2,2,4)')




![png](Matplotlib_17_1.png)


### Statistics 
* histogram  
* scatter plot  
* bar charts  
* pie charts  
* error bar charts  


```python
np.random.seed(0)
```


```python
y = np.random.randn(1000)
plt.hist(y,25)
plt.show()
```


![png](Matplotlib_20_0.png)



```python
x = np.random.randn(1000)
y = 3 * x + 4
plt.scatter(x, y)
```




    <matplotlib.collections.PathCollection at 0x117603208>




![png](Matplotlib_21_1.png)



```python
size = 50 * abs(np.random.randn(1000))
colors = np.random.randn(1000)
plt.scatter(x, y, s=size, c=colors)
plt.show()
```


![png](Matplotlib_22_0.png)



```python
plt.bar([1,2,3],[4,2,6])
plt.show()
```


![png](Matplotlib_23_0.png)



```python
x = [20,30,50]
labels = ['cat', 'dog', 'sheep']
plt.pie(x, labels=labels)
plt.show()
```


![png](Matplotlib_24_0.png)



```python
x = np.arange(0,4,0.2)
y = np.exp(-x)
e = 0.1 * abs(np.random.randn(len(y)))
plt.errorbar(x, y, yerr=e, fmt='.-')
plt.show()
```


![png](Matplotlib_25_0.png)


### Cool
* contour map
* 3D graph
* animation


```python
def f(x,y):
    return (1-x/2+x**2+y**5)*np.exp(-x**2-y**2)

n = 256
x = np.linspace(-3,3,n)
y = np.linspace(-3,3,n)
X,Y = np.meshgrid(x,y)

#plt.axes([0.025,0.025,0.95,0.95])

plt.contourf(X, Y, f(X,Y), 8, alpha=.75, cmap=plt.cm.hot)
```




    <matplotlib.contour.QuadContourSet at 0x11785ecc0>




![png](Matplotlib_27_1.png)



```python
x = np.arange(-5, 5, 0.1)
y = np.arange(-5, 5, 0.1)
xx, yy = np.meshgrid(x, y, sparse=True)
z = np.sin(xx**2 + yy**2) / (xx**2 + yy**2)
h = plt.contourf(x,y,z)
```


![png](Matplotlib_28_0.png)



```python
plt.imshow(f(X,Y))
```




    <matplotlib.image.AxesImage at 0x116262780>




![png](Matplotlib_29_1.png)



```python
from mpl_toolkits.mplot3d import Axes3D

fig = plt.figure()
ax = Axes3D(fig)
X = np.arange(-3, 3, 0.25)
Y = np.arange(-3, 3, 0.25)
X, Y = np.meshgrid(X, Y)
R = np.sqrt(X**2 + Y**2)
Z = np.sin(R)

ax.plot_surface(X, Y, Z, rstride=1, cstride=1, cmap='hot')
plt.show()
```


![png](Matplotlib_30_0.png)



```python
def update(frame):
    global P, C, S

    # Every ring is made more transparent
    C[:,3] = np.maximum(0, C[:,3] - 1.0/n)

    # Each ring is made larger
    S += (size_max - size_min) / n

    # Reset ring specific ring (relative to frame number)
    i = frame % 50
    P[i] = np.random.uniform(0,1,2)
    S[i] = size_min
    C[i,3] = 1

    # Update scatter object
    scat.set_edgecolors(C)
    scat.set_sizes(S)
    scat.set_offsets(P)

    # Return the modified object
    return scat,
```


```python
#%matplotlib notebook
from matplotlib.animation import FuncAnimation


fig = plt.figure(figsize=(6,6), facecolor='white')
ax = fig.add_axes([0,0,1,1], frameon=False, aspect=1)

n = 50
size_min = 50
size_max = 50*50

# Ring position
P = np.random.uniform(0,1,(n,2))

# Ring colors
C = np.ones((n,4)) * (0,0,0,1)
# Alpha color channel goes from 0 (transparent) to 1 (opaque)
C[:,3] = np.linspace(0,1,n)

# Ring sizes
S = np.linspace(size_min, size_max, n)

# Scatter plot
scat = ax.scatter(P[:,0], P[:,1], s=S, lw = 0.5,
                  edgecolors = C, facecolors='None')

# Ensure limits are [0,1] and remove ticks
ax.set_xlim(0,1), ax.set_xticks([])
ax.set_ylim(0,1), ax.set_yticks([])
animation = FuncAnimation(fig, update, interval=10, blit=True, frames=200)
plt.show()
```


![png](Matplotlib_32_0.png)

