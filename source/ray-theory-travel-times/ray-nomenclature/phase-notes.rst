震相名解析
==========

实际上唯一识别震相的应该是其射线参数和射线路径，震相名只是人们用于记住这些震相的代号而已。
不同软件/个人对于同一个震相可能定义不同的震相名，对于不同震相也可能定义同一震相名。

大家公认的标准是 IASPEI 标准：http://www.isc.ac.uk/standards/phases/。
我们主要基于 IASPEI 标准讨论一下地壳震相名，地壳震相也是震相解析中最麻烦的内容。

IASPEI 在命名地壳震相假设地球是两层地壳模型。当然，实际地壳不一定是两层，也可能是三层地壳。
但是我们一般使用的全球 1D 参考模型，比如 PREM、AK135、IASP91 等，都是两层模型。例如 IASP91
的地壳厚度是 35 km，其中上地壳厚度是 20 km::

    $ cat /opt/TauP-2.4.5/StdModels/iasp91.tvel
    IASPEI91 S Model (67 values to cmb)
    2      0.000    5.8000    3.3600    2.7200
    3     20.000    5.8000    3.3600    2.7200
    4     20.000    6.5000    3.7500    2.9200
    5     35.000    6.5000    3.7500    2.9200
    6     35.000    8.0400    4.4700    3.3198

.. warning::

   如果使用三层或单层地壳模型计算走时，需要了解不同软件解析出的地壳震相名到底代表啥。

一般认为大陆上地壳是花岗岩质（\ **g**\ ranite），下地壳是玄武岩质（\ **b**\ asalt）。
所以，Pg 和 Pb 里的 **g** 和 **b** 也就是指代 **g**\ ranite 和 **b**\ asalt。
需要注意的是大陆地壳成分并不一定是花岗岩质和玄武岩质。地震学软件里使用 **g** 和 **b** 只是
用于区别地壳震相，也可以用其他标识符。

.. warning::

   不同地震学软件的 Pg 和 Pb 不一定遵守 IASPEI 标准的，可能类似，可能完全不同。

   IASPEI 的 Pg：

     At short distances, either an upgoing P wave from a source in the upper crust or a P wave bottoming in the upper crust. At larger distances also arrivals caused by multiple P-wave reverberations inside the whole crust with a group velocity around 5.8 km/s.

   TauP 定义的 Pg 与 IASPEI 定义有所区别，比如 `Phase naming in obspy.taup <https://docs.obspy.org/packages/obspy.taup.html#phase-naming-in-obspy-taup>`__
   
     ray turning in the crust

   因此，TauP 里并没有 Pb 震相名。

需要注意的是 IASPEI 定义的 Pg 包括了大震中距的情况，即地壳内部多次 P 波混响产生的震相
（群速度约为 5.8 km/s）。这种 Pg 严格说来算不算体波，我也清楚。IASPEI 还定义了 Rg，
即 Short-period crustal Rayleigh wave。Rg 是不是就是大震中距的 Pg，笔者目前还不秦楚。
大多数地震学软件考虑的是小震中距的 Pg。

地壳 S 波震相名规则类似 P 波。例如，Sg 也分为小震中距和大震中距的情况。Lg 震相是不是就是
大震中距的 Sg，笔者目前还不清楚。 
