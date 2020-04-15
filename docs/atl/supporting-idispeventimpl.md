---
title: 支援 IDispEventImpl
ms.date: 11/04/2016
helpviewer_keywords:
- event sink maps, declaring
- IDispEventImpl class, advising and unadvising
- SINK_ENTRY macro
- type libraries, importing
- ATL, IDispEventImpl support in COM objects
- BEGIN_SINK_MAP macro
- IDispEventImpl class, declaring
ms.assetid: b957f930-6a5b-4598-8e4d-8027759957e7
ms.openlocfilehash: 31beff30a067416f71029c18051f214c8d4429de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329315"
---
# <a name="supporting-idispeventimpl"></a>支援 IDispEventImpl

範本類[IDispEventImpl](../atl/reference/idispeventimpl-class.md)可用於為ATL類中的連接點接收器提供支援。 連接點接收器允許類處理從外部 COM 物件觸發的事件。 這些連接點接收器使用事件接收器映射映射,由類提供。

要正確實現類的連接點接收器,必須完成以下步驟:

- 匯入每個外部物件的類型庫

- 宣告`IDispEventImpl`介面

- 宣告事件接收器對應

- 建議並取消建議連接點

實現連接點接收器所涉及的步驟都通過僅修改類的標頭檔 (.h) 來完成。

## <a name="importing-the-type-libraries"></a>匯入型別庫

對於要處理的事件的每個外部物件,必須導入類型庫。 此步驟定義可處理的事件,並提供聲明事件接收器映射時使用的資訊。 [#import](../preprocessor/hash-import-directive-cpp.md)指令可用於實現此目的。 為將支援的`#import`每個調度介面添加所需的指令行到類的標頭檔 (.h)。

以下範例匯入外部 COM 伺服器的型`MSCAL.Calendar.7`態庫 ( ):

[!code-cpp[NVC_ATL_Windowing#141](../atl/codesnippet/cpp/supporting-idispeventimpl_1.h)]

> [!NOTE]
> 對於將支援的每個外部`#import`類型庫,必須具有單獨的語句。

## <a name="declaring-the-idispeventimpl-interfaces"></a>宣告 IDispEventImpl 介面

現在,您已經導入了每個調度介面的類型庫,您需要為每個外部調度介面聲明單獨的`IDispEventImpl`介面。 通過為每個外部物件添加`IDispEventImpl`介面聲明來修改類的聲明。 有關參數的詳細資訊,請參閱[IDispEventImpl](../atl/reference/idispeventimpl-class.md)。

以下代碼聲明兩個連接點接收器,對於`DCalendarEvents`介面,對於由類`CMyCompositCtrl2`實現的 COM 物件:

[!code-cpp[NVC_ATL_Windowing#142](../atl/codesnippet/cpp/supporting-idispeventimpl_2.h)]

## <a name="declaring-an-event-sink-map"></a>宣告事件接收器對應

為了使事件通知由正確的函數處理,類必須將每個事件路由到其正確的處理程式。 這是通過聲明事件接收器映射來實現的。

ATL 提供了多個宏[,BEGIN_SINK_MAP、END_SINK_MAP](reference/composite-control-macros.md#begin_sink_map)[END_SINK_MAP](reference/composite-control-macros.md#end_sink_map)和[SINK_ENTRY_EX,](reference/composite-control-macros.md#sink_entry_ex)使此映射更容易。 標準格式如下:

```cpp
BEGIN_SINK_MAP(comClass)
  SINK_ENTRY_EX(id, iid, dispid, func)
  . . . //additional external event entries
END_SINK_MAP()
```

以下範例宣告有兩個事件處理程式的事件接收器對應:

[!code-cpp[NVC_ATL_Windowing#136](../atl/codesnippet/cpp/supporting-idispeventimpl_3.h)]

實現已接近完成。 最後一步是建議和取消通知外部介面。

## <a name="advising-and-unadvising-the-idispeventimpl-interfaces"></a>為 IDispEventImpl 介面提供諮詢和取消建議

最後一步是實現一種方法,該方法將在適當的時候通知(或不建議)所有連接點。 在外部用戶端和對象之間發生通信之前,必須執行此建議。 在物件變得可見之前,對象支援的每個外部調度介面都會查詢出發介面。 建立連接,並使用對傳出介面的引用來處理來自物件的事件。 此過程稱為"建議」。

在物件完成外部介面后,應通知傳出介面它們不再被類使用。 此過程稱為"不建議"

由於 COM 物件的獨特性質,此過程在細節和執行之間因實現而異。 這些詳細資訊超出了本主題的範圍,並且未涉及。

## <a name="see-also"></a>另請參閱

[ATL COM 物件的基礎知識](../atl/fundamentals-of-atl-com-objects.md)
