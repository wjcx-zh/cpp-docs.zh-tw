---
title: "使用 Lambda、函式物件和限制函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 25346cc9-869d-4ada-aad3-e2228cad3d6c
caps.latest.revision: 10
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 Lambda、函式物件和限制函式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您想要在加速器上執行的 C\+\+ AMP 程式碼會指定為引數，隨呼叫傳遞至 [parallel\_for\_each](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md) 方法。  您可以提供 Lambda 運算式或函式物件 \(functor\) 做為該引數。  此外，Lambda 運算式或函式物件還可以呼叫 C\+\+ AMP 限制函式。  本主題使用陣列加法演算法示範 lambda、 函式物件，以及受限制的函式。  下列範例會示範不具有 C\+\+ AMP 程式碼的演算法。  已建立兩個長度相同的一維陣列。  對應的整數項目會加入並儲存於第三個一維陣列中。  不會使用 C\+\+ AMP。  
  
```cpp  
  
void CpuMethod() {  
  
    int aCPP[] = {1, 2, 3, 4, 5};  
    int bCPP[] = {6, 7, 8, 9, 10};  
    int sumCPP[5];  
  
    for (int idx = 0; idx < 5; idx++)  
    {  
        sumCPP[idx] = aCPP[idx] + bCPP[idx];  
    }  
  
    for (int idx = 0; idx < 5; idx++)  
    {  
        std::cout << sumCPP[idx] << "\n";  
    }  
}  
  
```  
  
## Lambda 運算式  
 使用 Lambda 運算式是使用 C\+\+ AMP 來重寫程式碼最直接的方式。  
  
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
        }  
    );  
  
    for (int i = 0; i < 5; i++) {  
        std::cout << sum[i] << "\n";  
    }  
}  
  
```  
  
 Lambda 運算式必須包含一個索引參數，而且必須包含`restrict(amp)`。  在範例中，[array\_view](../../parallel/amp/reference/array-view-class.md) `sum` 物件排名為 1。  因此， lambda 陳述式的參數是排序為 1 的[索引](../../parallel/amp/reference/index-class.md)物件 。  在執行階段，lambda 運算式會對 [array\_view](../../parallel/amp/reference/array-view-class.md) 物件中的每個項目執行一次。  如需詳細資訊，請參閱[Lambda 運算式語法](../../cpp/lambda-expression-syntax.md)。  
  
## Function 物件  
 插入函式物件，就可以把加速器對應到程式碼。  
  
```cpp  
  
class AdditionFunctionObject  
{  
public:  
    AdditionFunctionObject(const array_view<int, 1>& a,  
        const array_view<int, 1>& b,  
        const array_view<int, 1>& sum  
    )  
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
        AdditionFunctionObject(a, b, sum)  
    );  
  
    for (int i = 0; i < 5; i++) {  
        std::cout << sum[i] << "\n";  
    }  
}  
  
```  
  
 函式物件必須包含一個建構函式，而且必須包含函式呼叫運算子多載。  函式呼叫運算子必須包含一個索引參數。  函式物件的執行個體會做為第二個引數傳遞給 [parallel\_for\_each](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md) 方法。  在此範例中，三個 [array\_view](../../parallel/amp/reference/array-view-class.md) 物件會傳遞至函式物件建構函式。  [array\_view](../../parallel/amp/reference/array-view-class.md) 物件 `sum` 排名為 1。  因此，函式呼叫運算子的參數是排序為 1 的[索引](../../parallel/amp/reference/index-class.md)物件。  在執行階段，此函式會對 [array\_view](../../parallel/amp/reference/array-view-class.md) 物件中的每個項目執行一次。  如需詳細資訊，請參閱[函式呼叫](../../cpp/function-call-cpp.md)與[STL 中的函式物件](../../standard-library/function-objects-in-the-stl.md)。  
  
## C\+\+ AMP 限制函式  
 您可以建立受限制的函式並從 lambda 運算式或函式物件呼叫該函式，進一步把加速器對應程式碼。  下列程式碼範例示範如何從 lambda 運算式呼叫受限的功能。  
  
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
        }  
    );  
  
    for (int i = 0; i < 5; i++) {  
        std::cout << sum[i] << "\n";  
    }  
}  
  
```  
  
 受限制的函式必須包含`restrict(amp)`且符合[restrict \(C\+\+ AMP\)](../../cpp/restrict-cpp-amp.md)所述的限制。  
  
## 請參閱  
 [C\+\+ AMP \(C\+\+ Accelerated Massive Parallelism\)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [Lambda 運算式語法](../../cpp/lambda-expression-syntax.md)   
 [函式呼叫](../../cpp/function-call-cpp.md)   
 [STL 中的函式物件](../../standard-library/function-objects-in-the-stl.md)   
 [restrict \(C\+\+ AMP\)](../../cpp/restrict-cpp-amp.md)