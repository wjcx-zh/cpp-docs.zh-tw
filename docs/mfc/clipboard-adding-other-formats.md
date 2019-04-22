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
ms.openlocfilehash: 182abe71ccc9552c113ebb114b4351178e48b096
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58766843"
---
# <a name="clipboard-adding-other-formats"></a>剪貼簿：加入其他格式

本主題說明如何擴充支援的格式，特別是針對 OLE 支援的清單。 本主題[剪貼簿：複製和貼上資料](../mfc/clipboard-copying-and-pasting-data.md)說明支援複製並貼上剪貼簿中所需的最小實作。 這是所有您所實作，放在剪貼簿上的唯一格式是否**CF_METAFILEPICT**， **CF_EMBEDSOURCE**， **CF_OBJECTDESCRIPTOR**，且可能**CF_LINKSOURCE**。 大部分的應用程式需要更多格式剪貼簿上的，於這三個。

##  <a name="_core_registering_custom_formats"></a> 登錄自訂格式

若要建立您自己自訂的格式，請遵循註冊任何自訂剪貼簿格式時，會使用相同的程序： 的格式名稱傳遞給**RegisterClipboardFormat**函式，並使用它的傳回值的格式識別碼。

##  <a name="_core_placing_formats_on_the_clipboard"></a> 將格式放在剪貼簿

若要新增更多格式所放在剪貼簿上，您必須覆寫`OnGetClipboardData`在您從其中衍生的類別中的函式`COleClientItem`或`COleServerItem`（取決於要複製的資料是否使用原生）。 在此函式中，您應該使用下列程序。

#### <a name="to-place-formats-on-the-clipboard"></a>將剪貼簿上的格式

1. 建立 `COleDataSource` 物件。

1. 要加入的支援格式清單中的原生資料格式，藉由呼叫的函式中傳遞此資料來源`COleDataSource::CacheGlobalData`。

1. 加入標準的格式，藉由呼叫`COleDataSource::CacheGlobalData`每一個您想要支援的標準格式。

在 MFC OLE 範例程式會使用這項技術[HIERSVR](../overview/visual-cpp-samples.md) (檢查`OnGetClipboardData`成員函式**CServerItem**類別)。 在此範例中唯一的差別在於並未實作該步驟三，因為 HIERSVR 不支援任何其他標準的格式。

### <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [OLE 資料物件和資料來源以及一致的資料傳輸](../mfc/data-objects-and-data-sources-ole.md)

- [OLE 拖放](../mfc/drag-and-drop-ole.md)

- [OLE](../mfc/ole-background.md)

## <a name="see-also"></a>另請參閱

[剪貼簿：使用 OLE 剪貼簿機制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)
