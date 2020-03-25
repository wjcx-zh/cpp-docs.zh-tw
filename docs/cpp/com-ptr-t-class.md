---
title: _com_ptr_t 類別
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t
helpviewer_keywords:
- _com_ptr_t class
ms.assetid: 3753a8a0-03d4-4cfd-8a9a-74872ea53971
ms.openlocfilehash: eeaab22ded537cbbb211a79596b8383251af3ab7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189896"
---
# <a name="_com_ptr_t-class"></a>_com_ptr_t 類別

**Microsoft 專屬**

**_Com_ptr_t**物件會封裝 com 介面指標，並稱為「智慧型」指標。 這個樣板類別會透過對 `IUnknown` 成員函式的函式呼叫來管理資源配置和解除配置： `QueryInterface`、`AddRef`和 `Release`。

智慧型指標通常是由 _COM_SMARTPTR_TYPEDEF 巨集提供的 typedef 定義所參考。 這個宏會採用介面名稱和 IID，並使用介面的名稱加上尾碼 `Ptr`，宣告 **_com_ptr_t**的特製化。 例如：

```cpp
_COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
```

宣告 **_com_ptr_t**特製化 `IMyInterfacePtr`。

一組函式樣板（而不是這個樣板類別的[成員）支援](../cpp/relational-function-templates.md)與比較運算子右邊的智慧型指標進行比較。

### <a name="construction"></a>建築業

|||
|-|-|
|[_com_ptr_t](../cpp/com-ptr-t-com-ptr-t.md)|結構 **_com_ptr_t**物件。|

### <a name="low-level-operations"></a>低階作業

|||
|-|-|
|[AddRef](../cpp/com-ptr-t-addref.md)|在封裝的介面指標上呼叫 `IUnknown` 的 `AddRef` 成員函式。|
|[附加](../cpp/com-ptr-t-attach.md)|封裝這個智慧型指標類型的一般介面指標。|
|[CreateInstance](../cpp/com-ptr-t-createinstance.md)|指定 `CLSID` 或 `ProgID`，建立物件的新實例。|
|[卸離](../cpp/com-ptr-t-detach.md)|擷取和傳回封裝的介面指標。|
|[GetActiveObject](../cpp/com-ptr-t-getactiveobject.md)|指定 `CLSID` 或 `ProgID`，附加至物件的現有實例。|
|[GetInterfacePtr](../cpp/com-ptr-t-getinterfaceptr.md)|傳回封裝的介面指標。|
|[QueryInterface](../cpp/com-ptr-t-queryinterface.md)|在封裝的介面指標上呼叫 `IUnknown` 的 `QueryInterface` 成員函式。|
|[版本](../cpp/com-ptr-t-release.md)|在封裝的介面指標上呼叫 `IUnknown` 的 `Release` 成員函式。|

### <a name="operators"></a>操作員

|||
|-|-|
|[operator =](../cpp/com-ptr-t-operator-equal.md)|將新值指派給現有的 **_com_ptr_t**物件。|
|[operators = =、！ =、\<、>、\<=、> =](../cpp/com-ptr-t-relational-operators.md)|將智慧型指標物件與另一個智慧型指標、一般介面指標或 NULL 進行比較。|
|[擷取器](../cpp/com-ptr-t-extractors.md)|擷取封裝的 COM 介面指標。|

**END Microsoft 特定的**

## <a name="requirements"></a>需求

**標頭：** \<comip.h. h >

**Lib：** comsuppw.lib 或 comsuppwd.lib （請參閱[/zc： Wchar_t （Wchar_t 是原生類型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)以取得詳細資訊）

## <a name="see-also"></a>另請參閱

[編譯器 COM 支援類別](../cpp/compiler-com-support-classes.md)
