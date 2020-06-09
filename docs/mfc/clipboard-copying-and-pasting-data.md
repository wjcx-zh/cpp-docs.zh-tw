---
title: 剪貼簿：複製和貼上資料
ms.date: 11/04/2016
helpviewer_keywords:
- Clipboard, copying data to
- Clipboard, pasting
ms.assetid: 580e10be-241f-4f9f-94cf-8302edc5beef
ms.openlocfilehash: ed3056ec4fb3d3098870a03522d3bf17f41fbe34
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620697"
---
# <a name="clipboard-copying-and-pasting-data"></a>剪貼簿：複製和貼上資料

本主題描述在 OLE 應用程式中執行剪貼簿的複製和貼上所需的最小工作。 建議您先閱讀[資料物件和資料來源（OLE）](data-objects-and-data-sources-ole.md)主題，再繼續進行。

您必須先提供函式來處理 [編輯] 功能表上的 [複製]、[剪下] 和 [貼上] 選項，才可以執行複製或貼入。

## <a name="copying-or-cutting-data"></a><a name="_core_copying_or_cutting_data"></a>複製或剪下資料

#### <a name="to-copy-data-to-the-clipboard"></a>將資料複製到剪貼簿

1. 判斷要複製的資料是否為原生資料，或為內嵌或連結的專案。

   - 如果資料是內嵌或連結的，請取得已選取之 `COleClientItem` 物件的指標。

   - 如果資料是原生的，而且應用程式是伺服器，請建立一個衍生自的新物件， `COleServerItem` 其中包含選取的資料。 否則，請建立 `COleDataSource` 資料的物件。

1. 呼叫選取專案的成員函式 `CopyToClipboard` 。

1. 如果使用者選擇剪下作業，而不是複製作業，請從您的應用程式中刪除選取的資料。

若要查看此順序的範例，請參閱 `OnEditCut` `OnEditCopy` MFC OLE 範例程式[OCLIENT](../overview/visual-cpp-samples.md)和[HIERSVR](../overview/visual-cpp-samples.md)中的和函式。 請注意，這些範例會維護目前選取之資料的指標，因此步驟1已經完成。

## <a name="pasting-data"></a><a name="_core_pasting_data"></a>貼上資料

貼上資料比較複雜，因為您必須選擇將資料貼入應用程式時所要使用的格式。

#### <a name="to-paste-data-from-the-clipboard"></a>從剪貼簿貼上資料

1. 在您的 view 類別中，執行 `OnEditPaste` 以處理使用者從 [編輯] 功能表選擇 [貼上] 選項。

1. 在函式中 `OnEditPaste` ，建立 `COleDataObject` 物件並呼叫其成員函式，將 `AttachClipboard` 此物件連結至剪貼簿上的資料。

1. 呼叫 `COleDataObject::IsDataAvailable` 以檢查特定的格式是否可用。

   或者，您可以使用 `COleDataObject::BeginEnumFormats` 來尋找其他格式，直到找出最適合您的應用程式。

1. 執行格式的貼上。

如需其運作方式的範例，請參閱 `OnEditPaste` MFC OLE 範例程式[OCLIENT](../overview/visual-cpp-samples.md)和[HIERSVR](../overview/visual-cpp-samples.md)中定義的 view 類別中的成員函式的執行。

> [!TIP]
> 將貼上作業分隔成自己的函式的主要優點是，在拖放作業期間，將資料放在應用程式中時，可以使用相同的貼上程式碼。 如同在 OCLIENT 和 HIERSVR 中，您的函式 `OnDrop` 也可以呼叫 `DoPasteItem` ，重複使用撰寫的程式碼來執行貼上作業。

若要處理 [編輯] 功能表上的 [貼上特殊] 選項，請參閱[OLE 中](dialog-boxes-in-ole.md)的主題對話方塊。

### <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [新增其他格式](clipboard-adding-other-formats.md)

- [OLE 資料物件和資料來源以及一致的資料傳輸](data-objects-and-data-sources-ole.md)

- [OLE 拖放](drag-and-drop-ole.md)

- [OLE](ole-background.md)

## <a name="see-also"></a>另請參閱

[剪貼簿：使用 OLE 剪貼簿機制](clipboard-using-the-ole-clipboard-mechanism.md)
