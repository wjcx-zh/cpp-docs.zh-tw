---
title: 文件樣板類別
ms.date: 11/04/2016
helpviewer_keywords:
- document templates [MFC], classes
ms.assetid: 901749e9-8048-44a0-b5e2-361554650a73
ms.openlocfilehash: dffde80093f98fc1c81a6c20dfaf92b82e3b4c78
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618989"
---
# <a name="document-template-classes"></a>文件樣板類別

當建立新的檔或視圖時，檔範本物件會協調檔、視圖和框架視窗物件的建立。

[CDocTemplate](reference/cdoctemplate-class.md)<br/>
檔範本的基類。 您永遠不會直接使用此類別;相反地，您會使用衍生自這個類別的其中一個檔範本類別。

[CMultiDocTemplate](reference/cmultidoctemplate-class.md)<br/>
多重文件介面（MDI）中檔的範本。 MDI 應用程式一次可以開啟多個檔。

[CSingleDocTemplate](reference/csingledoctemplate-class.md)<br/>
單一檔介面（SDI）中檔的範本。 SDI 應用程式一次只會開啟一份檔。

## <a name="related-class"></a>相關類別

[CCreateCoNtext](reference/ccreatecontext-structure.md)<br/>
檔範本傳遞至視窗建立功能的結構，可協調檔、視圖和框架視窗物件的建立。

## <a name="see-also"></a>另請參閱

[類別概觀](class-library-overview.md)
