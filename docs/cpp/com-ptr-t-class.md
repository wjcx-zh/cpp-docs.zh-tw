---
title: "_com_ptr_t 類別 | Microsoft Docs"
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
  - "_com_ptr_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_com_ptr_t 類別"
ms.assetid: 3753a8a0-03d4-4cfd-8a9a-74872ea53971
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_ptr_t 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 `_com_ptr_t` 物件會封裝 COM 介面指標，並且稱為「智慧型」指標。  這個樣板類別會透過對 **IUnknown** 成員函式的函式呼叫管理資源配置和解除配置：`QueryInterface`、`AddRef` 和 **Release**。  
  
 智慧型指標通常是由 **\_COM\_SMARTPTR\_TYPEDEF** 巨集提供的 typedef 定義所參考。  這個巨集會採用介面名稱和 IID，並且使用介面的名稱加上 `Ptr` 後置詞宣告 `_com_ptr_t` 的特製化。  例如：  
  
```  
_COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));  
```  
  
 會宣告 `_com_ptr_t` 特製化 **IMyInterfacePtr**。  
  
 一組[函式樣板](../cpp/relational-function-templates.md) \(不是這個樣板類別的成員\)，支援與比較運算子右方的智慧型指標進行比較。  
  
### 建構  
  
|||  
|-|-|  
|[\_com\_ptr\_t](../cpp/com-ptr-t-com-ptr-t.md)|建構 `_com_ptr_t` 物件。|  
  
### 低階作業  
  
|||  
|-|-|  
|[AddRef](../cpp/com-ptr-t-addref.md)|在封裝的介面指標上呼叫 **IUnknown** 的 `AddRef` 成員函式。|  
|[附加](../cpp/com-ptr-t-attach.md)|封裝這個智慧型指標類型的一般介面指標。|  
|[CreateInstance](../cpp/com-ptr-t-createinstance.md)|建立已指定 **CLSID** 或 **ProgID** 之物件的新執行個體。|  
|[中斷連結](../cpp/com-ptr-t-detach.md)|擷取和傳回封裝的介面指標。|  
|[GetActiveObject](../cpp/com-ptr-t-getactiveobject.md)|附加至已指定 **CLSID** 或 **ProgID** 之物件現有的執行個體。|  
|[GetInterfacePtr](../cpp/com-ptr-t-getinterfaceptr.md)|傳回封裝的介面指標。|  
|[QueryInterface](../cpp/com-ptr-t-queryinterface.md)|在封裝的介面指標上呼叫 **IUnknown** 的 `QueryInterface` 成員函式。|  
|[Release](../cpp/com-ptr-t-release.md)|在封裝的介面指標上呼叫 **IUnknown** 的 **Release** 成員函式。|  
  
### 運算子  
  
|||  
|-|-|  
|[運算子 \=](../cpp/com-ptr-t-operator-equal.md)|將新值指派給現有的 `_com_ptr_t` 物件。|  
|[運算子 \=\=、\!\=、\<、\>、\<\=、\>\=](../cpp/com-ptr-t-relational-operators.md)|將智慧型指標物件與另一個智慧型指標、一般介面指標或 **NULL** 進行比較。|  
|[擷取器](../cpp/com-ptr-t-extractors.md)|擷取封裝的 COM 介面指標。|  
  
## END Microsoft 特定的  
  
## 需求  
 **標頭：**comip.h  
  
 **Lib：**comsuppw.lib 或 comsuppwd.lib \(如需詳細資訊，請參閱 [\/Zc:wchar\_t \(wchar\_t 是原生類型\)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)\)  
  
## 請參閱  
 [編譯器 COM 支援類別](../cpp/compiler-com-support-classes.md)