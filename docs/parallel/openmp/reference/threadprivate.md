---
title: "threadprivate |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: threadprivate
dev_langs: C++
helpviewer_keywords: threadprivate OpenMP directive
ms.assetid: 3515aaed-6f9d-4d59-85eb-342378bea2d3
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 25685991222b02f4c622f344b06e9faaea4caf02
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="threadprivate"></a>threadprivate
指定在執行緒私用變數。  
  
## <a name="syntax"></a>語法  
  
```  
#pragma omp threadprivate(var)  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 `var`  
 您想要私用對執行緒的變數以逗號分隔清單。 `var`必須是全域或命名空間的範圍變數或靜態區域變數。  
  
## <a name="remarks"></a>備註  
 `threadprivate`指示詞可支援不含 OpenMP 子句。  
  
 如需詳細資訊，請參閱[2.7.1 threadprivate 指示詞](../../../parallel/openmp/2-7-1-threadprivate-directive.md)。  
  
 `threadprivate`指示詞根據[執行緒](../../../cpp/thread.md)`__declspec`屬性; 限制**__declspec （thread)**套用至`threadprivate`。  
  
 您無法使用`threadprivate`中任何會透過載入的 DLL [LoadLibrary](http://msdn.microsoft.com/library/windows/desktop/ms684175)。  這包括已用載入的 Dll [/DELAYLOAD （延遲載入匯入）](../../../build/reference/delayload-delay-load-import.md)，這也會使用**LoadLibrary**。  
  
 您可以使用`threadprivate`在處理序啟動時以靜態方式載入的 DLL 中。  
  
 因為`threadprivate`根據**__declspec （thread)**、`threadprivate`變數會存在於任何啟動程序，不只是由在平行區域產生的執行緒小組的一部分的執行緒的執行緒。  這是要留意，因為您可能會注意到，例如，建構函式的實作詳細資料`threadprivate`呼叫通常則預期更多的使用者定義型別。  
  
 A `threadprivate` destructable 類型的變數不能保證具有呼叫其解構函式。  例如:   
  
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
  
 使用者無權以從屬平行區域的執行緒會終止時控制。  如果當處理序結束時，執行緒將不會知道處理序結束，而不會針對呼叫解構函式，這些執行緒存在於`threaded_var`結束以外的任何執行緒上 （這裡，主執行緒）。  讓程式碼不應倚賴的正確解構`threadprivate`變數。  
  
## <a name="example"></a>範例  
 如需使用範例`threadprivate`，請參閱[私人](../../../parallel/openmp/reference/private-openmp.md)。  
  
## <a name="see-also"></a>請參閱  
 [指示詞](../../../parallel/openmp/reference/openmp-directives.md)