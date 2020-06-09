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
ms.openlocfilehash: 52089364a6be423c69a7031cd0d99e1924de1444
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626068"
---
# <a name="clipboard-adding-other-formats"></a>剪貼簿：加入其他格式

本主題說明如何擴充支援的格式清單，特別是針對 OLE 支援。 剪貼簿[：複製和](clipboard-copying-and-pasting-data.md)貼上資料一節說明支援從剪貼簿複製和貼上所需的最小執行。 如果這是您要執行的工作，則在剪貼簿上唯一的格式為**CF_METAFILEPICT**、 **CF_EMBEDSOURCE**、 **CF_OBJECTDESCRIPTOR**，而且可能**CF_LINKSOURCE**。 大部分的應用程式在剪貼簿上所需的格式會超過這三個。

## <a name="registering-custom-formats"></a><a name="_core_registering_custom_formats"></a>註冊自訂格式

若要建立您自己的自訂格式，請遵循註冊任何自訂剪貼簿格式時所使用的相同程式：將格式的名稱傳遞給**RegisterClipboardFormat**函式，並使用其傳回值做為格式識別碼。

## <a name="placing-formats-on-the-clipboard"></a><a name="_core_placing_formats_on_the_clipboard"></a>將格式放在剪貼簿上

若要將更多格式加入至剪貼簿上的位置，您必須覆寫 `OnGetClipboardData` 衍生自或的類別中的函式 `COleClientItem` `COleServerItem` （視要複製的資料是否為原生而定）。 在此函數中，您應該使用下列程式。

#### <a name="to-place-formats-on-the-clipboard"></a>將格式放在剪貼簿上

1. 建立 `COleDataSource` 物件。

1. 將此資料來源傳遞至函式，此函式會藉由呼叫，將您的原生資料格式加入至支援的格式清單 `COleDataSource::CacheGlobalData` 。

1. 藉由 `COleDataSource::CacheGlobalData` 針對您想要支援的每個標準格式呼叫來新增標準格式。

這項技術用於 MFC OLE 範例程式[HIERSVR](../overview/visual-cpp-samples.md) （檢查 `OnGetClipboardData` **CServerItem**類別的成員函式）。 此範例唯一的差別在於，不會執行步驟3，因為 HIERSVR 不支援其他標準格式。

### <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [OLE 資料物件和資料來源以及一致的資料傳輸](data-objects-and-data-sources-ole.md)

- [OLE 拖放](drag-and-drop-ole.md)

- [OLE](ole-background.md)

## <a name="see-also"></a>另請參閱

[剪貼簿：使用 OLE 剪貼簿機制](clipboard-using-the-ole-clipboard-mechanism.md)
