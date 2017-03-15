---
title: "IID_PPV_ARGS_Helper 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/IID_PPV_ARGS_Helper"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IID_PPV_ARGS_Helper 函式"
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# IID_PPV_ARGS_Helper 函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

確認指定的引數型別是從 `IUnknown` 介面衍生。  
  
> [!IMPORTANT]
>  這個樣板特殊化支援 WRL 基礎結構，而且並不是要讓您直接從程式碼來使用。  請使用 [IID\_PPV\_ARGS](http://msdn.microsoft.com/library/windows/desktop/ee330727.aspx)  
  
## 語法  
  
```  
template<  
   typename T  
>  
void** IID_PPV_ARGS_Helper(  
   _Inout_ Microsoft::WRL::Details::ComPtrRef<T> pp  
);  
```  
  
#### 參數  
 `T`  
 `pp`引數的型別。  
  
 `pp`  
 雙重間接取值指標。  
  
## 傳回值  
 引數 `pp` 轉換成指標到指標的 `void`。  
  
## 備註  
 如果樣板參數 `T` 不是從`IUnknown`衍生，就會產生編譯時期錯誤。  
  
## 需求  
 **標題:** client.h  
  
## 請參閱  
 [Reference \(Windows Runtime Library\)](http://msdn.microsoft.com/zh-tw/00000000-0000-0000-0000-000000000000)