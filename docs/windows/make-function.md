---
title: "Make 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Make"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Make 函式"
ms.assetid: 66704143-df99-4a95-904d-ed99607e1034
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Make 函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

初始化指定的 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 類別。  使用這個函式例示相同模組中定義的元件。  
  
## 語法  
  
```  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5,  
   typename TArg6,  
   typename TArg7,  
   typename TArg8,  
   typename TArg9  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3,  
   TArg4 &&arg4,  
   TArg5 &&arg5,  
   TArg6 &&arg6,  
   TArg7 &&arg7,  
   TArg8 &&arg8,  
   TArg9 &&arg9  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5,  
   typename TArg6,  
   typename TArg7,  
   typename TArg8  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3,  
   TArg4 &&arg4,  
   TArg5 &&arg5,  
   TArg6 &&arg6,  
   TArg7 &&arg7,  
   TArg8 &&arg8  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5,  
   typename TArg6,  
   typename TArg7  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3,  
   TArg4 &&arg4,  
   TArg5 &&arg5,  
   TArg6 &&arg6,  
   TArg7 &&arg7  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5,  
   typename TArg6  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3,  
   TArg4 &&arg4,  
   TArg5 &&arg5,  
   TArg6 &&arg6  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3,  
   TArg4 &&arg4,  
   TArg5 &&arg5  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3,  
   TArg4 &&arg4  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2  
);  
template <  
   typename T,  
   typename TArg1  
>  
ComPtr<T> Make(  
   TArg1 &&arg1  
);  
template <  
   typename T  
>  
ComPtr<T> Make();  
```  
  
#### 參數  
 `T`  
 繼承自 `WRL::RuntimeClass`的使用者特定的類別。  
  
 `TArg1`  
 傳遞至指定的執行階段的類別引數 1 的型別。  
  
 `TArg2`  
 傳遞至指定的執行階段的類別引數 2 的型別。  
  
 `TArg3`  
 傳遞至指定的執行階段的類別引數 3 的型別。  
  
 `TArg4`  
 傳遞至指定的執行階段的類別引數 4 的型別。  
  
 `TArg5`  
 傳遞至指定的執行階段的類別引數 5 的型別。  
  
 `TArg6`  
 傳遞至指定的執行階段的類別引數 6 的型別。  
  
 `TArg7`  
 傳遞至指定的執行階段的類別引數 7 的型別。  
  
 `TArg8`  
 傳遞至指定的執行階段的類別引數 8 的型別。  
  
 `TArg9`  
 傳遞至指定的執行階段的類別引數 9 的型別。  
  
 `arg1`  
 傳遞至指定的執行階段類別的引數 1。  
  
 `arg2`  
 傳遞至指定的執行階段類別的引數 2。  
  
 `arg3`  
 傳遞至指定的執行階段類別的引數 3。  
  
 `arg4`  
 傳遞至指定的執行階段類別的引數 4。  
  
 `arg5`  
 傳遞至指定的執行階段類別的引數 5。  
  
 `arg6`  
 傳遞至指定的執行階段類別的引數 6。  
  
 `arg7`  
 傳遞至指定的執行階段類別的引數 7。  
  
 `arg8`  
 傳遞至指定的執行階段類別的引數 8。  
  
 `arg9`  
 傳遞至指定的執行階段類別的引數 9。  
  
## 傳回值  
 `ComPtr<T>` 物件，如果成功;則為，否則為 `nullptr`。  
  
## 備註  
 請參閱 [如何：直接執行個體化 WRL 元件](../windows/how-to-instantiate-wrl-components-directly.md) 認識這個函式和 [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md) 的差異及範例。  
  
## 需求  
 **標頭：**implements.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)