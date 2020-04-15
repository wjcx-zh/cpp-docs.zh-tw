---
title: 剪貼簿：複製和貼上資料
ms.date: 11/04/2016
helpviewer_keywords:
- Clipboard, copying data to
- Clipboard, pasting
ms.assetid: 580e10be-241f-4f9f-94cf-8302edc5beef
ms.openlocfilehash: 74348dd3e790cceada9aafd718464694997316ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374561"
---
# <a name="clipboard-copying-and-pasting-data"></a>剪貼簿：複製和貼上資料

本主題介紹在 OLE 應用程式中實現複製和貼上從剪貼簿所需的最小工作。 建議您在繼續操作之前閱讀[「資料物件和數據來源 (OLE)」](../mfc/data-objects-and-data-sources-ole.md)主題。

在可以實現複製或粘貼之前,必須首先提供函數來處理"編輯"功能表上的"複製"、"剪切"和"貼貼"選項。

## <a name="copying-or-cutting-data"></a><a name="_core_copying_or_cutting_data"></a>複製或切割資料

#### <a name="to-copy-data-to-the-clipboard"></a>複製到剪貼簿

1. 確定要複製的數據是本機數據還是嵌入或連結項。

   - 如果資料是嵌入或連結的,請獲取指向已選擇`COleClientItem`物件的指標。

   - 如果數據是本機數據,並且應用程式是伺服器,請創建一個從`COleServerItem`包含所選數據派生的新物件。 否則,為數據`COleDataSource`創建物件。

1. 調用所選項的成員`CopyToClipboard`函數。

1. 如果用戶選擇了「剪切」操作而不是「複製」操作,請從應用程式中刪除所選數據。

要查看`OnEditCut`此序列的範例,請參閱 MFC`OnEditCopy`OLE 範例程式[OCLIENT](../overview/visual-cpp-samples.md)和[HIERSVR](../overview/visual-cpp-samples.md)中的和函數。 請注意,這些示例維護指向當前選定數據的指標,因此步驟 1 已完成。

## <a name="pasting-data"></a><a name="_core_pasting_data"></a>貼上資料

貼上資料比複製資料要複雜得多,因為您需要選擇要在將資料貼上到應用程式中的格式。

#### <a name="to-paste-data-from-the-clipboard"></a>貼上剪貼簿中的資料

1. 在檢視類中,實現`OnEditPaste`處理使用者從"編輯"功能表中選擇"粘貼"選項。

1. 在`OnEditPaste`函數中,創建`COleDataObject`一個對象`AttachClipboard`並調用其成員函數以將此物件連結到剪貼簿上的數據。

1. 呼叫`COleDataObject::IsDataAvailable`以檢查特定格式是否可用。

   或者,您可以使用`COleDataObject::BeginEnumFormats`查找其他格式,直到找到最適合您的應用程式。

1. 執行格式的粘貼。

有關其工作原理的示例,請參閱 MFC OLE`OnEditPaste`範例程式[OCLIENT](../overview/visual-cpp-samples.md)和[HIERSVR](../overview/visual-cpp-samples.md)中定義的視圖類中成員函數的實現。

> [!TIP]
> 將貼上操作分離到其自己的函數的主要好處是,在拖放操作期間,當數據在應用程式中丟棄時,可以使用相同的粘貼代碼。 與 OCLIENT 和`OnDrop`HIERSVR`DoPasteItem`中一樣 ,函數還可以調用 ,重用編寫的代碼來實現粘貼操作。

要處理「編輯」選單上的「貼上特殊」選項,請參閱[OLE 中的主題對話框](../mfc/dialog-boxes-in-ole.md)。

### <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [新增其他格式](../mfc/clipboard-adding-other-formats.md)

- [OLE 資料物件和資料來源以及一致的資料傳輸](../mfc/data-objects-and-data-sources-ole.md)

- [OLE 拖放](../mfc/drag-and-drop-ole.md)

- [OLE](../mfc/ole-background.md)

## <a name="see-also"></a>另請參閱

[剪貼簿：使用 OLE 剪貼簿機制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)
