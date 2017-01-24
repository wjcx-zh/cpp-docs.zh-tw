---
title: "_bstr_t 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_bstr_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_bstr_t 類別"
  - "BSTR 物件"
  - "BSTR 物件, COM 封裝"
ms.assetid: 58841fef-fe21-4a84-aab9-780262b5201f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _bstr_t 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 `_bstr_t` 物件封裝了 [BSTR 資料類型](http://msdn.microsoft.com/zh-tw/1b2d7d2c-47af-4389-a6b6-b01b7e915228)。  類別會適時透過 **SysAllocString** 和 **SysFreeString** 及其他 `BSTR` 應用程式開發介面的函式呼叫，管理資源配置和解除配置。  `_bstr_t` 類別會使用參考計數避免過多的額外負荷。  
  
### 建構  
  
|||  
|-|-|  
|[\_bstr\_t](../cpp/bstr-t-bstr-t.md)|建構 `_bstr_t` 物件。|  
  
### 作業  
  
|||  
|-|-|  
|[Assign](../cpp/bstr-t-assign.md)|將 `BSTR` 複製到 `_bstr_t` 所包裝的 `BSTR` 中。|  
|[附加](../cpp/bstr-t-attach.md)|將 `_bstr_t` 包裝函式連結至 `BSTR`。|  
|[copy](../cpp/bstr-t-copy.md)|建構已封裝 `BSTR` 的複本。|  
|[中斷連結](../cpp/bstr-t-detach.md)|傳回 `_bstr_t` 所包裝的 `BSTR`，並將 `BSTR` 與 `_bstr_t` 中斷連結。|  
|[GetAddress](../cpp/bstr-t-getaddress.md)|指向 `_bstr_t` 所包裝的 `BSTR`。|  
|[GetBSTR](../cpp/bstr-t-getbstr.md)|指向由 `_bstr_t` 所包裝之 `BSTR` 的開頭。|  
|[length](../cpp/bstr-t-length.md)|傳回 `_bstr_t` 中的字元數。|  
  
### 運算子  
  
|||  
|-|-|  
|[運算子 \=](../cpp/bstr-t-operator-equal.md)|將新值指派給現有的 `_bstr_t` 物件。|  
|[運算子 \+\=](../cpp/bstr-t-operator-add-equal-plus.md)|將字元附加至 `_bstr_t` 物件的結尾。|  
|[運算子 \+](../cpp/bstr-t-operator-add-equal-plus.md)|串連兩個字串。|  
|[運算子 \!](../cpp/bstr-t-operator-logical-not.md)|檢查封裝的 `BSTR` 是否為 **NULL** 字串。|  
|[運算子 \=\=、\!\=、\<、\>、\<\=、\>\=](../cpp/bstr-t-relational-operators.md)|比較兩個 `_bstr_t` 物件。|  
|[運算子 wchar\_t\* &#124; char\*](../cpp/bstr-t-wchar-t-star-bstr-t-char-star.md)|將指標擷取至封裝的 Unicode 或多位元組的 `BSTR` 物件。|  
  
## END Microsoft 特定的  
  
## 需求  
 **標頭：**comutil.h  
  
 **Lib：**comsuppw.lib 或 comsuppwd.lib \(如需詳細資訊，請參閱 [\/Zc:wchar\_t \(wchar\_t 是原生類型\)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)\)  
  
## 請參閱  
 [編譯器 COM 支援類別](../cpp/compiler-com-support-classes.md)