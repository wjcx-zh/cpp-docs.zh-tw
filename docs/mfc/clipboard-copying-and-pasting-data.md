---
title: 剪貼簿：複製和貼上資料
ms.date: 11/04/2016
helpviewer_keywords:
- Clipboard, copying data to
- Clipboard, pasting
ms.assetid: 580e10be-241f-4f9f-94cf-8302edc5beef
ms.openlocfilehash: 7f22418b4006bcb9fac1d4430660c8721bc7e903
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437033"
---
# <a name="clipboard-copying-and-pasting-data"></a>剪貼簿：複製和貼上資料

本主題說明實作複製和貼上從剪貼簿 OLE 應用程式所需的最少工作。 建議您閱讀[資料物件和資料來源 (OLE)](../mfc/data-objects-and-data-sources-ole.md)主題後再繼續。

您可以實作複製或貼上之前，您必須先提供函數來處理的複製、 剪下和貼上的選項，在 [編輯] 功能表上。

##  <a name="_core_copying_or_cutting_data"></a> 複製或剪下資料

#### <a name="to-copy-data-to-the-clipboard"></a>若要將資料複製到剪貼簿

1. 決定是否要複製的資料是原生資料，或內嵌或連結的項目。

   - 如果資料是內嵌或連結，取得的指標`COleClientItem`已選取的物件。

   - 如果資料是原生應用程式是伺服器，建立新的物件衍生自`COleServerItem`包含選取的資料。 否則，請建立`COleDataSource`資料物件。

1. 呼叫選取的項目`CopyToClipboard`成員函式。

1. 如果使用者選擇剪下的作業，而不是複製作業，請從您的應用程式中刪除選取的資料。

若要查看這個序列的範例，請參閱`OnEditCut`並`OnEditCopy`函式，在 MFC OLE 範例程式[OCLIENT](../visual-cpp-samples.md)並[HIERSVR](../visual-cpp-samples.md)。 請注意這些範例會維護目前選取的資料指標，所以已完成步驟 1。

##  <a name="_core_pasting_data"></a> 貼上資料

貼上資料是單純將它複製，因為您必須選擇要將資料貼到您的應用程式中使用的格式。

#### <a name="to-paste-data-from-the-clipboard"></a>若要貼上剪貼簿的資料

1. 在您的檢視類別，實作`OnEditPaste`處理使用者從 [編輯] 功能表中選擇 [貼上] 選項。

1. 在 `OnEditPaste`函式中，建立`COleDataObject`物件並呼叫其`AttachClipboard`成員函式，此物件連結到剪貼簿上的資料。

1. 呼叫`COleDataObject::IsDataAvailable`來檢查是否以特定格式。

   或者，您可以使用`COleDataObject::BeginEnumFormats`必須尋求其他格式，直到您找到其中一個最適合您的應用程式。

1. 執行貼上作業的格式。

如需其運作方式的範例，請參閱 < 實作`OnEditPaste`MFC OLE 範例程式中定義的檢視類別的成員函式[OCLIENT](../visual-cpp-samples.md)並[HIERSVR](../visual-cpp-samples.md)。

> [!TIP]
>  分隔成自己的函式貼上作業的主要優點是將資料放入您拖放作業期間的應用程式時，可以使用相同的貼上程式碼。 OCLIENT 和 HIERSVR，如同您`OnDrop`函式也可以呼叫`DoPasteItem`，重複使用來實作貼上作業所撰寫的程式碼。

若要處理 [編輯] 功能表上的 選擇性貼上選項，請參閱主題[對話方塊，在 OLE 中](../mfc/dialog-boxes-in-ole.md)。

### <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [加入其他格式](../mfc/clipboard-adding-other-formats.md)

- [OLE 資料物件和資料來源以及一致的資料傳輸](../mfc/data-objects-and-data-sources-ole.md)

- [OLE 拖放](../mfc/drag-and-drop-ole.md)

- [OLE](../mfc/ole-background.md)

## <a name="see-also"></a>另請參閱

[剪貼簿：使用 OLE 剪貼簿機制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)

