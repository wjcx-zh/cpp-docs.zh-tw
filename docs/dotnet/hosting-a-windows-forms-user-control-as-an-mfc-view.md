---
title: "裝載 Windows Form 使用者控制項為 MFC 檢視 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms controls [C++], hosting as an MFC view
- hosting Windows Forms control [C++]
ms.assetid: 43c02ab4-1366-434c-a980-0b19326d6ea0
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7e4e0b7bc081d3b16b3f9aa55719d298f710cdab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="hosting-a-windows-forms-user-control-as-an-mfc-view"></a>將 Windows Form 使用者控制項裝載為 MFC 檢視
MFC 使用 CWinFormsView 類別來裝載 Windows Form 使用者控制項在 MFC 檢視中。 MFC Windows Form 檢視是 ActiveX 控制項。 使用者控制項裝載為子系的原生的檢視，並佔用整個工作區的原生的檢視。  
  
 最終結果類似於所使用的模型[CFormView 類別](../mfc/reference/cformview-class.md)。 這可讓您充分利用 Windows Form 設計工具和執行階段建立表單架構的豐富檢視。  
  
 MFC Windows Form 檢視是 ActiveX 控制項，因為它們沒有相同`hwnd`做為 MFC 檢視表。 也就不能當做傳遞指標[CView](../mfc/reference/cview-class.md)檢視。 一般情況下，使用 Windows Form 檢視和 Win32 較不依賴使用.NET Framework 方法。  
  
 顯示與 MFC 一起使用的 Windows Form 的範例應用程式，請參閱[MFC 和 Windows Form 整合](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en)。  
  
## <a name="in-this-section"></a>本節內容  
 [如何：建立使用者控制項並裝載 MDI 檢視](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)  
  
 [如何：新增命令傳送至 Windows Forms 控制項](../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)  
  
 [如何：呼叫 Windows Forms 控制項的屬性和方法](../dotnet/how-to-call-properties-and-methods-of-the-windows-forms-control.md)  
  
## <a name="see-also"></a>請參閱  
 [在 MFC 中使用 Windows Form 使用者控制項](../dotnet/using-a-windows-form-user-control-in-mfc.md)   
 [操作說明：撰寫複合控制項](/dotnet/framework/winforms/controls/how-to-author-composite-controls)