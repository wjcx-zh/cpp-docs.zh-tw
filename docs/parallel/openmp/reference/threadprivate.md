---
title: threadprivate |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- threadprivate
dev_langs:
- C++
helpviewer_keywords:
- threadprivate OpenMP directive
ms.assetid: 3515aaed-6f9d-4d59-85eb-342378bea2d3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9454b33348fa4e4bc2efaa609001201ea215a8c9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081984"
---
# <a name="threadprivate"></a>threadprivate
指定在執行緒私用變數。  
  
## <a name="syntax"></a>語法  
  
```  
#pragma omp threadprivate(var)  
```  
  
### <a name="parameters"></a>參數
  
*var*<br/>
您想要的執行緒設為私用變數的逗號分隔清單。 `var` 必須是全域或命名空間-範圍變數或靜態區域變數。  
  
## <a name="remarks"></a>備註  
 `threadprivate`指示詞可支援無 OpenMP 子句。  
  
 如需詳細資訊，請參閱 < [2.7.1 threadprivate 指示詞](../../../parallel/openmp/2-7-1-threadprivate-directive.md)。  
  
 `threadprivate`指示詞根據[執行緒](../../../cpp/thread.md)`__declspec`屬性，限制 **__declspec （thread)** 套用至`threadprivate`。  
  
 您無法使用`threadprivate`中將會透過載入的任何 DLL [LoadLibrary](https://msdn.microsoft.com/library/windows/desktop/ms684175)。  這包括已用載入的 Dll [/DELAYLOAD （延遲載入匯入）](../../../build/reference/delayload-delay-load-import.md)，這也會使用**LoadLibrary**。  
  
 您可以使用`threadprivate`在程序啟動時以靜態方式載入的 DLL 中。  
  
 因為`threadprivate`為基礎 **__declspec （thread)**、`threadprivate`變數會存在於任何啟動程序，不只是屬於執行緒小組在平行區域所繁衍的執行緒的執行緒。  這是您可能要留意，因為您可能會注意到，比方說，建構函式的實作細節`threadprivate`使用者定義型別呼叫通常則應該更多。  
  
 A `threadprivate` destructable 類型的變數不保證會有呼叫其解構函式。  例如:   
  
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
  
 使用者擁有並構成平行區域的執行緒將會結束時沒有任何控制項。  如果這些執行緒不存在時的處理序結束，執行緒才不會收到處理序結束時，解構函式不會針對呼叫`threaded_var`結束以外的任何執行緒上 (主執行緒中的 這裡）。  因此程式碼不應該仰賴適當解構`threadprivate`變數。  
  
## <a name="example"></a>範例  
 如需使用的範例`threadprivate`，請參閱 <<c2> [ 私人](../../../parallel/openmp/reference/private-openmp.md)。  
  
## <a name="see-also"></a>另請參閱  
 [指示詞](../../../parallel/openmp/reference/openmp-directives.md)