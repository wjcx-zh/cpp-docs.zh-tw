---
title: 支援 IDispEventImpl |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- IDispEventImpl
dev_langs:
- C++
helpviewer_keywords:
- event sink maps, declaring
- IDispEventImpl class, advising and unadvising
- SINK_ENTRY macro
- type libraries, importing
- ATL, IDispEventImpl support in COM objects
- BEGIN_SINK_MAP macro
- IDispEventImpl class, declaring
ms.assetid: b957f930-6a5b-4598-8e4d-8027759957e7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7d7bfd2690cf8f1ed692e6e21bf05b56e2280ce0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055659"
---
# <a name="supporting-idispeventimpl"></a>支援 IDispEventImpl

此範本類別[IDispEventImpl](../atl/reference/idispeventimpl-class.md)可用來在您的 ATL 類別中的連接點接收提供支援。 連接點接收可讓您的類別來處理從外部 COM 物件引發的事件。 這些連接點接收對應與事件接收對應，提供您的類別。

若要正確實作連接點接收為您的類別，您必須完成下列步驟：

- 匯入每個外部物件的型別程式庫

- 宣告`IDispEventImpl`介面

- 宣告事件接收對應

- 通知與取消通知的連接點

所有完成的修改僅標頭檔 (.h) 之類別中實作連接點接收所需的步驟。

## <a name="importing-the-type-libraries"></a>匯入類型程式庫

針對每個外部物件您想要處理的事件，您必須匯入類型程式庫。 此步驟中定義可以處理的事件，並提供可在宣告事件接收對應的資訊。 [#Import](../preprocessor/hash-import-directive-cpp.md)指示詞可用來完成這項作業。 加入必要`#import`指示詞行，您將會支援標頭檔 (.h) 類別的每個分派介面。

下列範例會匯入外部 COM 伺服器的類型程式庫 (`MSCAL.Calendar.7`):

[!code-cpp[NVC_ATL_Windowing#141](../atl/codesnippet/cpp/supporting-idispeventimpl_1.h)]

> [!NOTE]
>  您必須擁有個別`#import`陳述式，您將會支援每個外部型別程式庫。

## <a name="declaring-the-idispeventimpl-interfaces"></a>宣告 IDispEventImpl 介面

既然您已匯入每個分派介面的類型程式庫，您需要宣告個別`IDispEventImpl`為每個外部分派介面的介面。 修改您類別的宣告，藉由新增`IDispEventImpl`介面宣告的每個外部物件。 如需有關參數的詳細資訊，請參閱 < [IDispEventImpl](../atl/reference/idispeventimpl-class.md)。

下列程式碼宣告兩個連接點接收`DCalendarEvents`介面，由類別實作的 COM 物件`CMyCompositCtrl2`:

[!code-cpp[NVC_ATL_Windowing#142](../atl/codesnippet/cpp/supporting-idispeventimpl_2.h)]

## <a name="declaring-an-event-sink-map"></a>宣告事件接收對應

為了讓適當的函式所處理的事件通知，您的類別必須將每個事件路由至正確的處理常式。 做法是宣告事件接收對應。

ATL 提供數個巨集， [BEGIN_SINK_MAP](reference/composite-control-macros.md#begin_sink_map)， [END_SINK_MAP](reference/composite-control-macros.md#end_sink_map)，並[SINK_ENTRY_EX](reference/composite-control-macros.md#sink_entry_ex)，可讓此對應更容易。 標準的格式如下所示：

```cpp
BEGIN_SINK_MAP(comClass)
  SINK_ENTRY_EX(id, iid, dispid, func)
  . . . //additional external event entries
END_SINK_MAP()
```

下列範例會宣告兩個事件處理常式與事件接收對應：

[!code-cpp[NVC_ATL_Windowing#136](../atl/codesnippet/cpp/supporting-idispeventimpl_3.h)]

幾乎完成實作。 最後一個步驟是有關通知及取消通知的外部介面。

## <a name="advising-and-unadvising-the-idispeventimpl-interfaces"></a>通知和取消通知 IDispEventImpl 介面

最後一個步驟是實作的方法，將會通知 （或取消通知） 的所有連接點，在適當的時間。 必須完成這項建議，再進行外部用戶端與您的物件之間的通訊。 您的物件會變成可見之前，您物件所支援的每個外部分派介面便會查詢輸出介面。 建立連線，並用來處理來自物件的事件之輸出介面的參考。 此程序稱為 「 通知 」。

外部介面完成您的物件之後，輸出介面會獲知他們無法再使用您的類別。 此程序稱為 「 取消通知。 」

由於唯一的 COM 物件，此程序各有不同，在詳細資料和執行，實作之間。 這些詳細資料已超出本主題的範圍，而不寄。

## <a name="see-also"></a>另請參閱

[ATL COM 物件的基本概念](../atl/fundamentals-of-atl-com-objects.md)

