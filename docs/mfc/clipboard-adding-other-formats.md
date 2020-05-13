---
title: 剪貼簿：加入其他格式
ms.date: 11/04/2016
helpviewer_keywords:
- formats [MFC], Clipboard
- Clipboard, formats
- custom formats, placing on Clipboard
- custom formats
- registering custom Clipboard data formats
- custom Clipboard data formats
ms.assetid: aea58159-65ed-4385-aeaa-3d9d5281903b
ms.openlocfilehash: 6f4e159cc1b6918843d4a164dcca88500eb7b038
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374612"
---
# <a name="clipboard-adding-other-formats"></a>剪貼簿：加入其他格式

本主題介紹如何擴展支援的格式清單,尤其是 OLE 支援格式。 主題[剪貼簿:複製和粘貼數據](../mfc/clipboard-copying-and-pasting-data.md)描述了支援從剪貼簿複製和粘貼所需的最小實現。 如果這是您實現的所有格式,則剪貼簿上放置的唯一格式是**CF_METAFILEPICT、CF_EMBEDSOURCE、CF_OBJECTDESCRIPTOR,****CF_METAFILEPICT**並且可能**CF_LINKSOURCE。** **CF_OBJECTDESCRIPTOR** 大多數應用程式在剪貼簿上需要比這三種格式更多的格式。

## <a name="registering-custom-formats"></a><a name="_core_registering_custom_formats"></a>註冊自訂格式

要建立自己的自定義格式,請遵循註冊任何自定義剪貼簿格式時使用的相同過程:將格式的名稱傳遞給**RegisterClipboard 格式**函數,並將其返回值用作格式 ID。

## <a name="placing-formats-on-the-clipboard"></a><a name="_core_placing_formats_on_the_clipboard"></a>在剪貼簿上放置格式

要向放置在剪貼簿上的格式添加更多格式,必須覆蓋從或`OnGetClipboardData`或`COleClientItem``COleServerItem`派生的類中的函數(具體取決於要複製的數據是否為本機)。 在此函數中,應使用以下過程。

#### <a name="to-place-formats-on-the-clipboard"></a>將格式放在剪貼簿上

1. 建立 `COleDataSource` 物件。

1. 將此資料源傳遞給一個函數,該函數通過調用`COleDataSource::CacheGlobalData`將本機數據格式添加到受支援的格式清單中。

1. 以呼叫`COleDataSource::CacheGlobalData`要支援的每個標準格式來添加標準格式。

此技術用於 MFC OLE 範例程式[HIERSVR(](../overview/visual-cpp-samples.md)檢查`OnGetClipboardData` **CServerItem**類的成員函數)。 此示例中的唯一區別是,步驟 3 未實現,因為 HIERSVR 不支援其他標準格式。

### <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [OLE 資料物件和資料來源以及一致的資料傳輸](../mfc/data-objects-and-data-sources-ole.md)

- [OLE 拖放](../mfc/drag-and-drop-ole.md)

- [OLE](../mfc/ole-background.md)

## <a name="see-also"></a>另請參閱

[剪貼簿：使用 OLE 剪貼簿機制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)
