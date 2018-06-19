---
title: 配置 GDI 資源 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- resources [MFC], printing
- GDI objects [MFC], allocating during printing
- printing [MFC], allocating GDI resources
ms.assetid: cef7e94d-5a27-4aea-a9ee-8369fc895d3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 25f05c29c74756276cdf3fd1f88048b9a5b87fa7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343216"
---
# <a name="allocating-gdi-resources"></a>配置 GDI 資源
本文說明如何配置和取消配置列印所需的 Windows 圖形裝置介面 (GDI) 物件。  
  
> [!NOTE]
>  如需詳細資訊，請參閱 GDI + SDK 文件，網址： [ http://msdn.microsoft.com/library/default.aspurl=/library/gdicpp/GDIPlus/GDIPlus.asp ](http://msdn.microsoft.com/library/default.aspurl=/library/gdicpp/gdiplus/gdiplus.asp)。  
  
 假設您需要使用特定字型、畫筆或其他 GDI 物件進行列印，但不用於螢幕顯示。 在應用程式啟動時配置這些物件需要較多記憶體，因此不符合效益。 當應用程式未列印文件時，這些記憶體可能需要用於其他用途。 在列印開始時配置這些物件，然後在列印結束時加以刪除，是較理想的做法。  
  
 若要配置這些 GDI 物件，請覆寫[OnBeginPrinting](../mfc/reference/cview-class.md#onbeginprinting)成員函式。 此函式是適合此用途的原因有二： 架構會呼叫此函式一次開頭的每一個列印工作，而且不同於[OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)，此函式可以存取[CDC](../mfc/reference/cdc-class.md)物件代表印表機裝置驅動程式。 您也可以定義指向 GDI 物件的檢視類別中的成員變數在列印工作儲存使用這些物件 (例如， **CFont \*** 成員等等)。  
  
 若要使用您所建立的 GDI 物件，將其選取至印表機裝置內容中[OnPrint](../mfc/reference/cview-class.md#onprint)成員函式。 如果您的文件的不同頁面需要不同的 GDI 物件，您可以檢查`m_nCurPage`隸屬[CPrintInfo](../mfc/reference/cprintinfo-structure.md)結構，並據以選取 GDI 物件。 如果您的數個連續頁面需要某個 GDI 物件，Windows 會要求您在每次呼叫 `OnPrint` 時將其選取至裝置內容中。  
  
 若要取消配置這些 GDI 物件，覆寫[OnEndPrinting](../mfc/reference/cview-class.md#onendprinting)成員函式。 架構會每個列印工作結束時呼叫此函式，讓您有機會在應用程式回到其他工作之前取消配置列印特定 GDI 物件。  
  
## <a name="see-also"></a>另請參閱  
 [列印](../mfc/printing.md)   
 [如何完成預設列印](../mfc/how-default-printing-is-done.md)

