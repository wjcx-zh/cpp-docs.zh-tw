---
title: 使用 IDispEventSimpleImpl (ATL) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- IDispEventSimpleImpl
dev_langs:
- C++
helpviewer_keywords:
- IDispEventSimpleImpl class, using
ms.assetid: 8640ad1a-4bd0-40a5-b5e4-7322685d7aab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a47cef741e9db3237bbc9f6477cdf2863b38e4e3
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760366"
---
# <a name="using-idispeventsimpleimpl"></a>使用 IDispEventSimpleImpl

當使用`IDispEventSimpleImpl`來處理事件，您必須：

- 衍生您的類別，從[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)。

- 將事件接收對應新增至您的類別。

- 定義[_ATL_FUNC_INFO](../atl/reference/atl-func-info-structure.md)結構描述的事件。

- 將項目新增至事件接收對應使用[SINK_ENTRY_INFO](reference/composite-control-macros.md#sink_entry_info)巨集。

- 實作您想要處理的方法。

- 通知與取消通知的事件來源。

## <a name="example"></a>範例

下列範例會示範如何處理`DocumentChange`事件引發的 Word**應用程式**物件。 此事件上定義為方法`ApplicationEvents`dispinterface。

此範例是來自[ATLEventHandling 範例](../visual-cpp-samples.md)。  

```cpp
[ uuid(000209F7-0000-0000-C000-000000000046), hidden ]  
dispinterface ApplicationEvents {
properties:
methods:
    [id(0x00000001), restricted, hidden]
    void Startup();

    [id(0x00000002)]
    void Quit();

    [id(0x00000003)]
    void DocumentChange();
};
```

此範例會使用`#import`從 Word 的型別程式庫產生必要的標頭檔。 如果您想要與其他版本的 Word 中使用此範例中，您必須指定正確的 mso dll 檔案。 例如，Office 2000 提供 mso9.dll 和 OfficeXP 提供 mso.dll。 此程式碼被簡化從 stdafx.h 中：

[!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventsimpleimpl_1.h)]

在此範例中實際使用的類型程式庫的唯一資訊是這個字的 CLSID`Application`物件和 IID`ApplicationEvents`介面。 在編譯時期只使用此資訊。

下列程式碼會出現在 Simple.h。 相關的程式碼註解所註明：

[!code-cpp[NVC_ATL_EventHandlingSample#3](../atl/codesnippet/cpp/using-idispeventsimpleimpl_2.h)]

下列程式碼取自 Simple.cpp:

[!code-cpp[NVC_ATL_EventHandlingSample#4](../atl/codesnippet/cpp/using-idispeventsimpleimpl_3.cpp)]

## <a name="see-also"></a>另請參閱

[事件處理](../atl/event-handling-and-atl.md)   
[ATLEventHandling 範例](../visual-cpp-samples.md)

