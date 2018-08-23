---
title: RuntimeClass 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass
dev_langs:
- C++
helpviewer_keywords:
- RuntimeClass class
ms.assetid: d52f9d1a-98e5-41f2-a143-8fb629dd0727
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8f6cca23834eb889ecb83d91b40861b92fe922ad
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605980"
---
# <a name="runtimeclass-class"></a>RuntimeClass 類別

表示繼承指定的介面，並提供指定的 Windows 執行階段、 傳統 COM 和弱式參考支援 WinRT 或 COM 類別。

這個類別會提供 WinRT 及 COM 的類別，提供的實作的未定案實作`QueryInterface`， `AddRef`，`Release`等等管理模組的參考計數，並支援提供的 class factory可啟動的物件。

## <a name="syntax"></a>語法

```cpp
template <typename ...TInterfaces> class RuntimeClass
template <unsigned int classFlags, typename ...TInterfaces> class RuntimeClass;
```

### <a name="parameters"></a>參數

*classFlags*  
選擇性參數。 一或多個組合[RuntimeClassType](../windows/runtimeclasstype-enumeration.md)列舉值。 `__WRL_CONFIGURATION_LEGACY__`巨集可以定義變更 classFlags 專案中的所有執行階段類別的預設值。 如果定義，RuntimeClass 執行個體是非 agile 預設。 未定義，RuntimeClass 執行個體皆為敏捷式預設。 若要避免模稜兩可一律指定`Microsoft::WRL::FtmBase`中`TInterfaces`或`RuntimeClassType::InhibitFtmBase`。 請注意，如果 InhibitFtmBase 和 FtmBase 兩者都用物件將會是敏捷式軟體開發。

*TInterfaces*  
介面清單物件會實作超越`IUnknown`，`IInspectable`或其他介面受到[RuntimeClassType](../windows/runtimeclasstype-enumeration.md)。 它也可能會列出其他類別以值得注意的是衍生自`Microsoft::WRL::FtmBase`使敏捷式軟體開發的物件，並將它實作`IMarshal`。

## <a name="members"></a>成員

`RuntimeClassInitialize` 用來初始化物件，如果函式`MakeAndInitialize`樣板函式用來建構物件。 如果初始化失敗，，傳回 S_OK，如果物件已成功初始化或 COM 錯誤碼。 COM 錯誤程式碼會傳播的傳回值為`MakeAndInitialize`。 請注意，`RuntimeClassInitialize`方法不會呼叫如果`Make`樣板函式用來建構物件。

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[RuntimeClass::RuntimeClass 建構函式](../windows/runtimeclass-runtimeclass-constructor.md)|初始化 RuntimeClass 類別目前執行個體。|
|[RuntimeClass::~RuntimeClass 解構函式](../windows/runtimeclass-tilde-runtimeclass-destructor.md)|取消初始化 RuntimeClass 類別目前執行個體。|

## <a name="inheritance-hierarchy"></a>繼承階層

這是實作詳細資料。

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)