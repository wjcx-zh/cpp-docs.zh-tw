---
title: 剪貼簿： 加入其他格式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- formats [MFC], Clipboard
- Clipboard, formats
- custom formats, placing on Clipboard
- custom formats
- registering custom Clipboard data formats
- custom Clipboard data formats
ms.assetid: aea58159-65ed-4385-aeaa-3d9d5281903b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c28fd1d628d0aed79028e43d9cce383f3acbb4ae
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="clipboard-adding-other-formats"></a>剪貼簿：加入其他格式
本主題說明如何展開的清單支援的格式，特別是針對 OLE 支援。 本主題[剪貼簿： 複製和貼上資料](../mfc/clipboard-copying-and-pasting-data.md)說明支援複製及貼上剪貼簿中所需的最小實作。 如果這是所有您實作，就放在剪貼簿上只有格式`CF_METAFILEPICT`， **CF_EMBEDSOURCE**， **CF_OBJECTDESCRIPTOR**，且可能`CF_LINKSOURCE`。 大部分的應用程式需要比這三個剪貼簿格式。  
  
##  <a name="_core_registering_custom_formats"></a> 登錄自訂格式  
 若要建立您自己的自訂格式，請遵循相同的程序登錄任何自訂剪貼簿格式時，您會使用： 傳遞至格式的名稱**RegisterClipboardFormat**函式，並使用它的傳回值為格式識別碼。  
  
##  <a name="_core_placing_formats_on_the_clipboard"></a> 放置在剪貼簿格式  
 若要加入更多的格式與放在剪貼簿上，您必須覆寫`OnGetClipboardData`您從其中衍生的類別中的函式`COleClientItem`或`COleServerItem`（取決於要複製的資料是否使用原生）。 在這個函式，您應該使用下列程序。  
  
#### <a name="to-place-formats-on-the-clipboard"></a>將放在剪貼簿格式  
  
1.  建立 `COleDataSource` 物件。  
  
2.  若要加入的支援格式清單中的原生資料格式，藉由呼叫的函式傳遞此資料來源`COleDataSource::CacheGlobalData`。  
  
3.  新增標準格式，藉由呼叫`COleDataSource::CacheGlobalData`每一個您要支援的標準格式。  
  
 這項技術用於 MFC OLE 範例程式[HIERSVR](../visual-cpp-samples.md) (檢查`OnGetClipboardData`成員函式**CServerItem**類別)。 此範例中的唯一差異是 HIERSVR 支援其他標準格式，所以未實作步驟 3。  
  
### <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [OLE 資料物件和資料來源和制式資料傳輸](../mfc/data-objects-and-data-sources-ole.md)  
  
-   [OLE 拖放](../mfc/drag-and-drop-ole.md)  
  
-   [OLE](../mfc/ole-background.md)  
  
## <a name="see-also"></a>另請參閱  
 [剪貼簿：使用 OLE 剪貼簿機制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)

