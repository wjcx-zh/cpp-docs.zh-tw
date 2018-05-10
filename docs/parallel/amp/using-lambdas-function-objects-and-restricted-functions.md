---
title: 使用 Lambda、 函式物件和限制函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 25346cc9-869d-4ada-aad3-e2228cad3d6c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5e3e5ab742335cfd6bb47a5105995d7339c7c36a
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="using-lambdas-function-objects-and-restricted-functions"></a>使用 Lambda、函式物件和限制函式
做為引數的呼叫中指定您想要在加速器上執行的 c + + AMP 程式碼[parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each)方法。 您可以提供 lambda 運算式或函式物件 （仿函式），當做該引數。 此外，lambda 運算式或函式物件可以呼叫 c + + AMP 限制函式。 本主題會使用陣列加法演算法，來示範 lambda、 函式物件和限制函式。 下列範例會顯示沒有 c + + AMP 程式碼的演算法。 會建立兩個長度相同的 1 維陣列。 對應的整數項目都會加入，並儲存在第三個 1 維陣列。 不使用 c + + AMP。  
  
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
 使用 lambda 運算式是最直接的方式，來使用 c + + AMP 重寫程式碼。  
  
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
  
 Lambda 運算式必須包含一個索引參數，而且必須包含`restrict(amp)`。 在範例中， [array_view](../../parallel/amp/reference/array-view-class.md) `sum`物件具有陣序 1。 因此，lambda 陳述式的參數是[索引](../../parallel/amp/reference/index-class.md)具有陣序規範 1 的物件。 在執行階段，lambda 運算式會執行一次中每個元素[array_view](../../parallel/amp/reference/array-view-class.md)物件。 如需詳細資訊，請參閱[Lambda 運算式語法](../../cpp/lambda-expression-syntax.md)。  
  
## <a name="function-object"></a>Function 物件  
 您可以將對應程式碼分解成函式物件。  
  
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

 函式物件必須包含一個建構函式，而且必須包含的函式呼叫運算子多載。 函式呼叫運算子必須包含一個索引參數。 函式物件的執行個體做為第二個引數傳遞[parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each)方法。 在此範例中，三個[array_view](../../parallel/amp/reference/array-view-class.md)物件會傳遞給函式物件的建構函式。 [Array_view](../../parallel/amp/reference/array-view-class.md)物件`sum`的次序為 1。 因此，函式呼叫運算子的參數是[索引](../../parallel/amp/reference/index-class.md)具有陣序規範 1 的物件。 在執行階段，此函式會執行一次中每個元素[array_view](../../parallel/amp/reference/array-view-class.md)物件。 如需詳細資訊，請參閱[函式呼叫](../../cpp/function-call-cpp.md)和[c + + 標準程式庫中的函式物件](../../standard-library/function-objects-in-the-stl.md)。  
  
## <a name="c-amp-restricted-function"></a>C + + AMP 限制函式  
 您可以藉由建立受限的函式，並呼叫從 lambda 運算式或函式物件，進一步分解對應程式碼。 下列程式碼範例示範如何從 lambda 運算式呼叫的受限的函式。  
  
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
  
 受限的函式必須包含`restrict(amp)`符合所述的限制和[限制 (c + + AMP)](../../cpp/restrict-cpp-amp.md)。  
  
## <a name="see-also"></a>另請參閱  
 [C + + AMP (c + + Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [Lambda 運算式語法](../../cpp/lambda-expression-syntax.md)   
 [函式呼叫](../../cpp/function-call-cpp.md)   
 [C + + 標準程式庫中的函式物件](../../standard-library/function-objects-in-the-stl.md)   
 [restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)

