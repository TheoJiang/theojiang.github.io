---
title: IEnumerator.MoveNext
categories:
  - U3DC#
date: 2018-04-27 14:24:33
tags:
description: 
---

"虽然一直在用着C#做Unity3D开发，但是有的东西却没有去细究过。以后便持续对以前没有去深究的东西在这里做下小研究。
做Unity3D时一直在使用协程，协程有利用了IEnumerator,最近在项目中有看到单独的调用IEnumerator的情况，好奇下做了下研究。"

<!-- more -->


``` cs
using System;
using System.Collections;
namespace IEnumertorTest
{
    class Program
    {
        static void Main(string[] args)
        {
            Tclass t = new Tclass();
            t.begin();
        }
    }

    class Tclass
    {       
        public void begin()
        {
            IEnumerator t = test();
            t.MoveNext();
            Console.WriteLine(t.Current);
            t.MoveNext();
            Console.WriteLine(t.Current);
            t.MoveNext();
            Console.WriteLine(t.Current);
            t.MoveNext();
            Console.WriteLine(t.Current);
            
        }
        IEnumerator test()
        {
            Console.WriteLine("Hello World!111");
            yield return 0;
            Console.WriteLine("Hello World!222");
            yield return 1;
            Console.WriteLine("Hello World!333");
            yield return 2;
        } 
    }
}

```

输出结果：
```
Hello World!111
0
Hello World!222
1
Hello World!333
2
2
```

可知MoveNext的用处是执行下一代码段。
yeild return返回的类型为object, 如果是IEnumerator<T>则隐式转换为泛型类型参数。