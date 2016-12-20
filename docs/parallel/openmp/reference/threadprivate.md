---
title: "threadprivate | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "threadprivate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "threadprivate OpenMP directive"
ms.assetid: 3515aaed-6f9d-4d59-85eb-342378bea2d3
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# threadprivate
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

指定變數是專屬於一個執行緒。  
  
## 語法  
  
```  
#pragma omp threadprivate(var)  
```  
  
## 備註  
 其中，  
  
 `var`  
 您想要對執行緒私用變數以逗號分隔清單。  `var`必須是全域或命名空間的範圍變數或靜態區域變數。  
  
## 備註  
 `threadprivate`指示詞可支援任何 OpenMP 子句。  
  
 如需詳細資訊，請參閱 [2.7.1 threadprivate 指示詞](../../../parallel/openmp/2-7-1-threadprivate-directive.md)。  
  
 `threadprivate`指示詞根據[執行緒](../../../cpp/thread.md)`__declspec`屬性。 限制 **\_\_declspec\(thread\)** 適用於`threadprivate`。  
  
 您不能使用`threadprivate`任何會經由載入的 DLL 中 [LoadLibrary](http://msdn.microsoft.com/library/windows/desktop/ms684175)。  這包括所載入的 Dll [\/DELAYLOAD \(延遲載入匯入\)](../../../build/reference/delayload-delay-load-import.md)，它也會使用 **LoadLibrary**。  
  
 您可以使用`threadprivate`以靜態方式是在處理序啟動時載入的 DLL 中。  
  
 因為`threadprivate`根據 **\_\_declspec\(thread\)**、 `threadprivate`變數會存在於不只是藉由在平行區域繁衍執行緒小組的一部分的執行緒啟動過程中，在任何執行緒。  這是您可能想要特別注意，因為您可能會發現，比方說，建構函式的實作細節`threadprivate`通常在必須有那麼多個稱為 「 使用者定義型別。  
  
 A `threadprivate` destructable 型別的變數則無法保證能呼叫其解構函式。  例如：  
  
```  
struct MyType   
{  
    ~MyType();  
};  
  
MyType threaded_var;  
#pragma omp threadprivate(threaded_var)  
int main()   
{  
    #pragma omp parallel  
    {}  
}  
```  
  
 使用者有沒有任何控制項，當執行緒從屬平行區域會隨之終止。  如果這些執行緒存在，當處理序結束時，執行緒不會通知程序結束時，而不會呼叫解構函式的`threaded_var`在結束以外的任何執行緒上 \(這裡，呼叫這個方法\)。  讓程式碼與否適當解構時， `threadprivate`變數。  
  
## 範例  
 範例中使用的`threadprivate`，請參閱[私用](../../../parallel/openmp/reference/private-openmp.md)。  
  
## 請參閱  
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)