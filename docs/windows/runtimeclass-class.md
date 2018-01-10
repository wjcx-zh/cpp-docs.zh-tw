---
title: "RuntimeClass 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::RuntimeClass
dev_langs: C++
helpviewer_keywords: RuntimeClass class
ms.assetid: d52f9d1a-98e5-41f2-a143-8fb629dd0727
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d5c75492b55cd1c238798d3500e2157738c3c58f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="runtimeclass-class"></a>RuntimeClass 類別
表示繼承指定的介面，並提供指定的 Windows 執行階段、 傳統 COM 和弱式參考支援 WinRT 或 COM 類別。  
  
這個類別會提供 WinRT 及 COM 的類別，提供的實作的未定案實作`QueryInterface`， `AddRef`，`Release`等，管理之模組的參考計數，並可支援提供的 class factory可啟動的物件。
  
## <a name="syntax"></a>語法  
  
```
template <typename ...TInterfaces> class RuntimeClass
template <unsigned int classFlags, typename ...TInterfaces> class RuntimeClass;
```
  
#### <a name="parameters"></a>參數  
 `classFlags`  
選擇性參數。 一或多個組合[RuntimeClassType](../windows/runtimeclasstype-enumeration.md)列舉值。 `__WRL_CONFIGURATION_LEGACY__`巨集可以定義變更 classFlags 專案中的所有執行階段類別的預設值。 如果定義，RuntimeClass 執行個體是非 agile 的預設值。 未定義，RuntimeClass 執行個體是預設敏捷式軟體開發。 若要避免模稜兩可一定要指定在 Microsoft::WRL::FtmBase`TInterfaces`或 RuntimeClassType::InhibitFtmBase。 請注意，如果 InhibitFtmBase 和 FtmBase 同時使用物件會是 agile。
 
 `TInterfaces`  
超過 IUnknown、 IInspectable 或由其他介面的介面清單物件實作[RuntimeClassType](../windows/runtimeclasstype-enumeration.md)。 它也可能會列出從值得注意的是 Microsoft::WRL::FtmBase 以讓 agile 物件，並導致它實作 IMarshal 衍生其他類別。
  
## <a name="members"></a>成員  
`RuntimeClassInitialize`函式初始化物件，如果 MakeAndInitialize 樣板函式用來建構物件。 如果初始化失敗，，傳回 S_OK，如果物件已成功初始化或 COM 錯誤碼。 COM 錯誤程式碼會傳播做 MakeAndInitialize 的傳回值。 請注意，是否讓樣板函式用來建構物件不會呼叫 RuntimeClassInitialize 方法。

### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[RuntimeClass::RuntimeClass 建構函式](../windows/runtimeclass-runtimeclass-constructor.md)|初始化 RuntimeClass 類別的目前執行個體。|  
|[RuntimeClass::~RuntimeClass 解構函式](../windows/runtimeclass-tilde-runtimeclass-destructor.md)|取消初始化 RuntimeClass 類別的目前執行個體。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
這是實作詳細資料。
  
## <a name="requirements"></a>需求  
**標頭：** implements.h  
  
**命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>請參閱  
[Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)
