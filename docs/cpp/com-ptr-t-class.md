---
title: "_com_ptr_t 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_ptr_t
dev_langs:
- C++
helpviewer_keywords:
- _com_ptr_t class
ms.assetid: 3753a8a0-03d4-4cfd-8a9a-74872ea53971
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f9a17309ab08d50be1366b8db71798766b52baa9
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="comptrt-class"></a>_com_ptr_t 類別
**Microsoft 特定的**  
  
 `_com_ptr_t` 物件會封裝 COM 介面指標，並且稱為「智慧型」指標。 此範本類別管理資源配置和解除配置函式呼叫來透過**IUnknown**成員函式： `QueryInterface`， `AddRef`，和**發行**。  
  
 所提供的 typedef 定義所參考的智慧型指標通常**_COM_SMARTPTR_TYPEDEF**巨集。 這個巨集會採用介面名稱和 IID，並且使用介面的名稱加上 `_com_ptr_t` 後置詞宣告 `Ptr` 的特製化。 例如:   
  
```  
_COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));  
```  
  
 宣告`_com_ptr_t`特製化**IMyInterfacePtr**。  
  
 一組[函式範本](../cpp/relational-function-templates.md)，不屬於此範本類別，支援的比較運算子右側的智慧型指標比較。  
  
### <a name="construction"></a>建構  
  
|||  
|-|-|  
|[_com_ptr_t](../cpp/com-ptr-t-com-ptr-t.md)|建構 `_com_ptr_t` 物件。|  
  
### <a name="low-level-operations"></a>低階作業  
  
|||  
|-|-|  
|[AddRef](../cpp/com-ptr-t-addref.md)|呼叫`AddRef`成員函式**IUnknown**封裝的介面指標上。|  
|[Attach](../cpp/com-ptr-t-attach.md)|封裝這個智慧型指標類型的一般介面指標。|  
|[CreateInstance](../cpp/com-ptr-t-createinstance.md)|建立指定物件的新執行個體**CLSID**或**ProgID**。|  
|[Detach](../cpp/com-ptr-t-detach.md)|擷取和傳回封裝的介面指標。|  
|[GetActiveObject](../cpp/com-ptr-t-getactiveobject.md)|將附加至現有的執行個體的指定物件**CLSID**或**ProgID**。|  
|[GetInterfacePtr](../cpp/com-ptr-t-getinterfaceptr.md)|傳回封裝的介面指標。|  
|[QueryInterface](../cpp/com-ptr-t-queryinterface.md)|呼叫`QueryInterface`成員函式**IUnknown**封裝的介面指標上。|  
|[發行](../cpp/com-ptr-t-release.md)|呼叫**發行**成員函式**IUnknown**封裝的介面指標上。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[operator =](../cpp/com-ptr-t-operator-equal.md)|將新值指派給現有的 `_com_ptr_t` 物件。|  
|[運算子 = =、 ！ =、 \<，>， \<=、 > =](../cpp/com-ptr-t-relational-operators.md)|比較智慧型指標物件與另一個智慧型指標、 一般介面指標或**NULL**。|  
|[擷取器](../cpp/com-ptr-t-extractors.md)|擷取封裝的 COM 介面指標。|  
  
**結束 Microsoft 特定的**  
  
## <a name="requirements"></a>需求  
 **標頭：** \<comip.h >  
  
 **Lib:** comsuppw.lib 或 comsuppwd.lib (請參閱[/zc: wchar_t （wchar_t 是原生類型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)如需詳細資訊)  
  
## <a name="see-also"></a>請參閱  
 [編譯器 COM 支援類別](../cpp/compiler-com-support-classes.md)