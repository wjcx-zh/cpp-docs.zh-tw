---
title: 文件樣板類別
ms.date: 11/04/2016
f1_keywords:
- vc.classes.document
helpviewer_keywords:
- document templates [MFC], classes
ms.assetid: 901749e9-8048-44a0-b5e2-361554650a73
ms.openlocfilehash: 2589bc8f04e791f73529af91ffb148c2c717cd08
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164980"
---
# <a name="document-template-classes"></a>文件樣板類別

文件範本物件的文件、 檢視和框架視窗物件的新文件時建立或建立檢視。

[CDocTemplate](../mfc/reference/cdoctemplate-class.md)<br/>
文件範本基底類別。 您永遠不會直接; 使用這個類別相反地，您會使用其中一個衍生自這個類別的其他文件範本類別。

[CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)<br/>
在多重文件介面 (MDI) 的文件的範本。 MDI 應用程式可以有多個文件開啟一次。

[CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md)<br/>
在單一文件介面 (SDI) 中的文件的範本。 SDI 應用程式已開啟一次只能有一個文件。

## <a name="related-class"></a>相關的類別

[CCreateContext](../mfc/reference/ccreatecontext-structure.md)<br/>
結構傳遞至視窗建立函式，來協調建立文件、 檢視和框架視窗物件的文件範本。

## <a name="see-also"></a>另請參閱

[類別概觀](../mfc/class-library-overview.md)
