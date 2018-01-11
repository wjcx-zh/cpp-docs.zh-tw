---
title: "裝載 Windows 形成 MFC 對話方塊中的使用者控制 |Microsoft 文件"
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
- hosting Windows Forms control [C++]
- Windows Forms [C++], MFC support
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: da8e8a54947b329fe36eea5c80bdc13ba5cdfa74
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="hosting-a-windows-form-user-control-in-an-mfc-dialog-box"></a>將 Windows Form 使用者控制項裝載至 MFC 對話方塊中
MFC ActiveX 控制項是特殊類型裝載 Windows Form 控制項和使用 ActiveX 介面及屬性和方法的控制項與通訊<xref:System.Windows.Forms.Control>類別。 我們建議您使用.NET Framework 的屬性和方法在控制項上運作。  
  
 顯示與 MFC 一起使用的 Windows Form 的範例應用程式，請參閱[MFC 和 Windows Form 整合](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en)。  
  
> [!NOTE]
>  在目前版本中，`CDialogBar`物件無法裝載 Windows Form 控制項。  
  
## <a name="in-this-section"></a>本節內容  
 [如何：建立使用者控制項並裝載至對話方塊中](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)  
  
 [如何： 執行 DDX/DDV 資料繫結使用 Windows Form](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)  
  
 [如何：從原生 C++ 類別接收 Windows Forms 事件](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)  
  
## <a name="reference"></a>參考資料  
 [CWinFormsControl 類別](../mfc/reference/cwinformscontrol-class.md)&#124;[CDialog 類別](../mfc/reference/cdialog-class.md)&#124;[CWnd 類別](../mfc/reference/cwnd-class.md)&#124;<xref:System.Windows.Forms.Control>  
  
## <a name="see-also"></a>請參閱  
 [在 MFC 中使用 Windows Form 使用者控制項](../dotnet/using-a-windows-form-user-control-in-mfc.md)   
 [Windows Form/MFC 程式設計的差異](../dotnet/windows-forms-mfc-programming-differences.md)   
 [Windows Form 使用者控制項裝載為 MFC 檢視](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)   
 [將 Windows Forms 使用者控制項裝載成 MFC 對話方塊](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)