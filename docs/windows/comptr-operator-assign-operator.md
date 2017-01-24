---
title: "ComPtr::operator= 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/Microsoft::WRL::ComPtr::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator= 運算子"
ms.assetid: 1a0c2752-f7d8-4819-9443-07b88b69ef02
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtr::operator= 運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

將值指派給目前 ComPtr。  
  
## 語法  
  
```  
WRL_NOTHROW ComPtr& operator=(  
   decltype(__nullptr)  
);  
WRL_NOTHROW ComPtr& operator=(  
   _In_opt_ T *other  
);  
template <  
   typename U  
>  
WRL_NOTHROW ComPtr& operator=(  
   _In_opt_ U *other  
);  
WRL_NOTHROW ComPtr& operator=(  
   const ComPtr &other  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr& operator=(  
   const ComPtr<U>& other  
);  
WRL_NOTHROW ComPtr& operator=(  
   _Inout_ ComPtr &&other  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr& operator=(  
   _Inout_ ComPtr<U>&& other  
);  
```  
  
#### 參數  
 `U`  
 類別。  
  
 `other`  
 指標、參考、rvalue 參考型別或另一個 ComPtr。  
  
## 傳回值  
 對目前 ComPtr 的參考。  
  
## 備註  
 這個運算子的第一個版本指派 null 值套用至目前 ComPtr。  
  
 在第二個版本，如果指定的介面指標與目前 ComPtr 介面指標不同，第二個介面指標將被指派給目前 ComPtr。  
  
 在第三個版本，指派的介面指標將指派給目前 ComPtr。  
  
 在第四個版本，如果指派值的介面指標與目前 ComPtr 介面指標不同，第二個介面指標指派給目前 ComPtr。  
  
 第五個版本是複製運算子; ComPtr 的參考將指派給目前 ComPtr。  
  
 第六個版本是使用移動語意的複本運算子;為 ComPtr 的右值參考，如果有任何型別是靜態轉型再指派給目前 ComPtr。  
  
 第七個版本是使用移動語意的複本運算子;在型別為 `U` ComPtr 的右值參考為靜態轉型再指派給目前 ComPtr。  
  
## 需求  
 **標題:** client.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [ComPtr 類別](../windows/comptr-class.md)