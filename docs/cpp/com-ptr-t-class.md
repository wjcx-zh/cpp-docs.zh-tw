---
title: _com_ptr_t 類別
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t
helpviewer_keywords:
- _com_ptr_t class
ms.assetid: 3753a8a0-03d4-4cfd-8a9a-74872ea53971
ms.openlocfilehash: 2c299ea4a5aaabba847c85500a6023d7b112d492
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838499"
---
# <a name="_com_ptr_t-class"></a>_com_ptr_t 類別

**Microsoft 特定的**

**_Com_ptr_t**物件會封裝 com 介面指標，而且稱為「智慧型」指標。 此範本類別會透過對成員函式的函式呼叫來管理資源配置和解除配置 `IUnknown` ： `QueryInterface` 、 `AddRef` 和 `Release` 。

智慧型指標通常是由 _COM_SMARTPTR_TYPEDEF 巨集提供的 typedef 定義所參考。 此宏會採用介面名稱和 IID，並使用介面的名稱加上後置詞，宣告 **_com_ptr_t** 的特製化 `Ptr` 。 例如：

```cpp
_COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
```

宣告 **_com_ptr_t** 特製化 `IMyInterfacePtr` 。

一組函式 [範本](../cpp/relational-function-templates.md)，而不是此樣板類別的成員，支援與比較運算子右邊的智慧型指標進行比較。

### <a name="construction"></a>營造

| 名稱 | 描述 |
|-|-|
|[_com_ptr_t](../cpp/com-ptr-t-com-ptr-t.md)|結構 **_com_ptr_t** 物件。|

### <a name="low-level-operations"></a>低階作業

| 名稱 | 描述 |
|-|-|
|[AddRef](../cpp/com-ptr-t-addref.md)|`AddRef` `IUnknown` 在封裝的介面指標上呼叫的成員函式。|
|[附加](../cpp/com-ptr-t-attach.md)|封裝這個智慧型指標類型的一般介面指標。|
|[CreateInstance](../cpp/com-ptr-t-createinstance.md)|使用指定的或，建立物件的新 `CLSID` 實例 `ProgID` 。|
|[卸離](../cpp/com-ptr-t-detach.md)|擷取和傳回封裝的介面指標。|
|[GetActiveObject](../cpp/com-ptr-t-getactiveobject.md)|附加至給定或之物件的現有實例 `CLSID` `ProgID` 。|
|[GetInterfacePtr](../cpp/com-ptr-t-getinterfaceptr.md)|傳回封裝的介面指標。|
|[QueryInterface](../cpp/com-ptr-t-queryinterface.md)|`QueryInterface` `IUnknown` 在封裝的介面指標上呼叫的成員函式。|
|[版本](../cpp/com-ptr-t-release.md)|`Release` `IUnknown` 在封裝的介面指標上呼叫的成員函式。|

### <a name="operators"></a>運算子

| 名稱 | 描述 |
|-|-|
|[運算子 =](../cpp/com-ptr-t-operator-equal.md)|將新值指派給現有的 **_com_ptr_t** 物件。|
|[operators = =、！ =、 \<, > 、 \<=, >=](../cpp/com-ptr-t-relational-operators.md)|將智慧型指標物件與另一個智慧型指標、一般介面指標或 NULL 進行比較。|
|[擷取器](../cpp/com-ptr-t-extractors.md)|擷取封裝的 COM 介面指標。|

**結束 Microsoft 專有**

## <a name="requirements"></a>規格需求

**標頭：**\<comip.h>

**Lib：** comsuppw .lib 或 comsuppwd.lib .lib (請參閱 [/zc： Wchar_t (Wchar_t 是原生類型) ](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) 以取得詳細資訊) 

## <a name="see-also"></a>另請參閱

[編譯器 COM 支援類別](../cpp/compiler-com-support-classes.md)
