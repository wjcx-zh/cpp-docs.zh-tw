---
title: 使用 Lambda、函式物件和限制函式
ms.date: 11/04/2016
ms.assetid: 25346cc9-869d-4ada-aad3-e2228cad3d6c
ms.openlocfilehash: 0c72ae6f600fe73405481e34ab05b60f163e44d2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57288112"
---
# <a name="using-lambdas-function-objects-and-restricted-functions"></a>使用 Lambda、函式物件和限制函式

做為引數的呼叫中指定您想要在加速器上執行的 c + + AMP 程式碼[parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each)方法。 您可以提供 lambda 運算式或函式物件 (functor) 做為該引數。 此外，lambda 運算式或函式物件可以呼叫 c + + AMP 限定函式。 本主題使用陣列加法演算法示範 lambda、 函式物件和限制函式。 下列範例示範不需要 c + + AMP 程式碼的演算法。 會建立兩個 1 維度的陣列長度相同。 對應的整數項目會加入，並儲存在第三個 1 維陣列。 不使用 c + + AMP。

```cpp
void CpuMethod() {

    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5];

    for (int idx = 0; idx <5; idx++)
    {
        sumCPP[idx] = aCPP[idx] + bCPP[idx];
    }

    for (int idx = 0; idx <5; idx++)
    {
        std::cout <<sumCPP[idx] <<"\n";
    }
}
```

## <a name="lambda-expression"></a>Lambda 運算式

使用 lambda 運算式是使用 c + + AMP 來重寫程式碼最直接的方式。

```cpp
void AddArraysWithLambda() {
    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5];

    array_view<const int, 1> a(5, aCPP);

    array_view<const int, 1> b(5, bCPP);

    array_view<int, 1> sum(5, sumCPP);

    sum.discard_data();

    parallel_for_each(
        sum.extent,
        [=](index<1> idx) restrict(amp)
        {
             sum[idx] = a[idx] + b[idx];
        });

    for (int i = 0; i <5; i++) {
        std::cout <<sum[i] <<"\n";
    }
}
```

Lambda 運算式必須包含一個索引參數，而且必須包含`restrict(amp)`。 在範例中， [array_view](../../parallel/amp/reference/array-view-class.md) `sum`物件具有排名為 1。 因此，lambda 陳述式的參數是[index](../../parallel/amp/reference/index-class.md)排序為 1 的物件。 在執行階段，lambda 運算式會執行一次中每個元素[array_view](../../parallel/amp/reference/array-view-class.md)物件。 如需詳細資訊，請參閱 < [Lambda 運算式語法](../../cpp/lambda-expression-syntax.md)。

## <a name="function-object"></a>Function 物件

您可以把加速器對應程式碼到函式物件。

```cpp
class AdditionFunctionObject
{
public:
    AdditionFunctionObject(const array_view<int, 1>& a,
    const array_view<int, 1>& b,
    const array_view<int, 1>& sum)
    : a(a), b(b), sum(sum)
    {
    }

    void operator()(index<1> idx) restrict(amp)
    {
        sum[idx] = a[idx] + b[idx];
    }

private:
    array_view<int, 1> a;
    array_view<int, 1> b;
    array_view<int, 1> sum;
};

void AddArraysWithFunctionObject() {
    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5];

    array_view<const int, 1> a(5, aCPP);

    array_view<const int, 1> b(5, bCPP);

    array_view<int, 1> sum(5, sumCPP);

    sum.discard_data();

    parallel_for_each(
        sum.extent,
        AdditionFunctionObject(a, b, sum));

    for (int i = 0; i <5; i++) {
        std::cout <<sum[i] <<"\n";
    }
}
```

函式物件必須包含一個建構函式，而且必須包含的函式呼叫運算子多載。 函式呼叫運算子必須包含一個索引參數。 函式物件的執行個體傳遞做為第二個引數[parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each)方法。 在此範例中，三個[array_view](../../parallel/amp/reference/array-view-class.md)物件會傳遞至函式物件的建構函式。 [Array_view](../../parallel/amp/reference/array-view-class.md)物件`sum`的次序為 1。 因此，函式呼叫運算子的參數是[index](../../parallel/amp/reference/index-class.md)排序為 1 的物件。 在執行階段，此函式會執行一次中每個元素[array_view](../../parallel/amp/reference/array-view-class.md)物件。 如需詳細資訊，請參閱 <<c0> [ 函式呼叫](../../cpp/function-call-cpp.md)並[c + + 標準程式庫中的函式物件](../../standard-library/function-objects-in-the-stl.md)。

## <a name="c-amp-restricted-function"></a>C + + AMP 限定函式

您可以藉由建立受限制的函式，並呼叫從 lambda 運算式或函式物件，進一步把加速器對應程式碼。 下列程式碼範例示範如何從 lambda 運算式呼叫受限的功能。

```cpp
void AddElementsWithRestrictedFunction(index<1> idx, array_view<int, 1> sum, array_view<int, 1> a, array_view<int, 1> b) restrict(amp)
{
    sum[idx] = a[idx] + b[idx];
}

void AddArraysWithFunction() {

    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5];

    array_view<int, 1> a(5, aCPP);

    array_view<int, 1> b(5, bCPP);

    array_view<int, 1> sum(5, sumCPP);

    sum.discard_data();

    parallel_for_each(
        sum.extent,
        [=](index<1> idx) restrict(amp)
        {
            AddElementsWithRestrictedFunction(idx, sum, a, b);
        });

    for (int i = 0; i <5; i++) {
        std::cout <<sum[i] <<"\n";
    }
}
```

受限制的函式必須包含`restrict(amp)`而且符合所述的限制[限制 (c + + AMP)](../../cpp/restrict-cpp-amp.md)。

## <a name="see-also"></a>另請參閱

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Lambda 運算式語法](../../cpp/lambda-expression-syntax.md)<br/>
[函式呼叫](../../cpp/function-call-cpp.md)<br/>
[C++ 標準程式庫的函式物件](../../standard-library/function-objects-in-the-stl.md)<br/>
[restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)
