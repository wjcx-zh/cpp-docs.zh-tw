---
title: 使用 RichEdit 1.0 控制項與 MFC |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- RichEdit 1.0 control
- rich edit controls, RichEdit 1.0
ms.assetid: 5a9060dd-44d8-4ef3-956e-16152f7e23d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d2d45de1c6bd986c2bf509ce601f80fcd3721599
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890307"
---
# <a name="using-the-richedit-10-control-with-mfc"></a>將 RichEdit 1.0 控制項與 MFC 一起使用
若要使用 RichEdit 控制項，您必須先呼叫[AfxInitRichEdit2](../mfc/reference/application-information-and-management.md#afxinitrichedit2)載入 RichEdit 2.0 控制項 (RICHED20。DLL)，或呼叫[AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit)載入較舊的 RichEdit 1.0 控制項 (RICHED32。DLL)。  
  
 您可以使用目前[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)類別與較舊的 RichEdit 1.0 控制項，但**CRichEditCtrl**只是要支援 RichEdit 2.0 控制項。 RichEdit 1.0 和 RichEdit 2.0 是非常類似，因為大部分的方法就會運作。不過請注意有一些差異 1.0 及 2.0 控制項，因此某些方法可能未正確運作，或完全無法運作。  
  
## <a name="requirements"></a>需求  
 MFC  
  
## <a name="see-also"></a>另請參閱  
 [對話方塊編輯器的疑難排解](../windows/troubleshooting-the-dialog-editor.md)   
 [對話方塊編輯器](../windows/dialog-editor.md)

