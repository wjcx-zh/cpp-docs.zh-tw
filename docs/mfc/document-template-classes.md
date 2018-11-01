---
title: 文件樣板類別
ms.date: 11/04/2016
f1_keywords:
- vc.classes.document
helpviewer_keywords:
- document templates [MFC], classes
ms.assetid: 901749e9-8048-44a0-b5e2-361554650a73
ms.openlocfilehash: b15263005f8bd6a8fdc9f9f29ea268fe8a6b95a3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448070"
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

