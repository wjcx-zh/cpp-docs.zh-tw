---
title: _com_ptr_t 類別
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t
helpviewer_keywords:
- _com_ptr_t class
ms.assetid: 3753a8a0-03d4-4cfd-8a9a-74872ea53971
ms.openlocfilehash: ce19dbc5f55460bb4bdbdee17f4fbbbcc8c6fd60
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547117"
---
# <a name="comptrt-class"></a>_com_ptr_t 類別

**Microsoft 專屬**

A **_com_ptr_t**物件會封裝 COM 介面指標，稱為 「 智慧型 」 指標。 此範本類別管理資源配置和解除配置函式呼叫，以透過`IUnknown`成員函式： `QueryInterface`， `AddRef`，和`Release`。

智慧型指標通常是由 _COM_SMARTPTR_TYPEDEF 巨集所提供的 typedef 定義參考。 這個巨集會採用介面名稱和 IID，並宣告的特製化 **_com_ptr_t**介面，再加上後的置字元的名稱取代`Ptr`。 例如: 

```cpp
_COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
```

宣告 **_com_ptr_t**特製化`IMyInterfacePtr`。

一組[函式範本](../cpp/relational-function-templates.md)，不屬於此範本類別，支援與比較運算子右方的智慧型指標的比較。

### <a name="construction"></a>建構

|||
|-|-|
|[_com_ptr_t](../cpp/com-ptr-t-com-ptr-t.md)|建構 **_com_ptr_t**物件。|

### <a name="low-level-operations"></a>低階作業

|||
|-|-|
|[AddRef](../cpp/com-ptr-t-addref.md)|呼叫`AddRef`成員函式`IUnknown`上封裝的介面指標。|
|[Attach](../cpp/com-ptr-t-attach.md)|封裝這個智慧型指標類型的一般介面指標。|
|[CreateInstance](../cpp/com-ptr-t-createinstance.md)|建立指定物件的新執行個體`CLSID`或`ProgID`。|
|[Detach](../cpp/com-ptr-t-detach.md)|擷取和傳回封裝的介面指標。|
|[GetActiveObject](../cpp/com-ptr-t-getactiveobject.md)|將附加至現有的執行個體的物件的給定`CLSID`或`ProgID`。|
|[GetInterfacePtr](../cpp/com-ptr-t-getinterfaceptr.md)|傳回封裝的介面指標。|
|[QueryInterface](../cpp/com-ptr-t-queryinterface.md)|呼叫`QueryInterface`成員函式`IUnknown`上封裝的介面指標。|
|[發行](../cpp/com-ptr-t-release.md)|呼叫`Release`成員函式`IUnknown`上封裝的介面指標。|

### <a name="operators"></a>運算子

|||
|-|-|
|[operator =](../cpp/com-ptr-t-operator-equal.md)|將新的值指派給現有 **_com_ptr_t**物件。|
|[運算子 = =、 ！ =、 \<，>， \<=、 > =](../cpp/com-ptr-t-relational-operators.md)|比較智慧型指標物件與另一個智慧型指標、 一般介面指標，或為 NULL。|
|[擷取器](../cpp/com-ptr-t-extractors.md)|擷取封裝的 COM 介面指標。|

**結束 Microsoft 專屬**

## <a name="requirements"></a>需求

**標頭：** \<comip.h >

**Lib:** comsuppw.lib 或 comsuppwd.lib (請參閱 < [/zc: wchar_t （wchar_t 是原生型別）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)如需詳細資訊)

## <a name="see-also"></a>另請參閱

[編譯器 COM 支援類別](../cpp/compiler-com-support-classes.md)