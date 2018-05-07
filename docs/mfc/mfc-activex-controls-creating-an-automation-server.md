---
title: MFC ActiveX 控制項： 建立 Automation 伺服程式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Automation servers [MFC], MFC ActiveX controls
- ActiveX controls [MFC], Automation server
- MFC ActiveX controls [MFC], Automation server
ms.assetid: e0c24ed2-d61c-49ad-a4fa-4e1098d1d39b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 617d84b8603467da74b21be8c2bfb2e6cb418f7b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-activex-controls-creating-an-automation-server"></a>MFC ActiveX 控制項：建立 Automation 伺服程式
您可以為 Automation 伺服程式為了以程式設計方式將該控制項內嵌在另一個應用程式和控制項中呼叫方法，從應用程式開發 MFC ActiveX 控制項。 這類控制項仍可裝載 ActiveX 控制項容器中。  
  
### <a name="to-create-a-control-as-an-automation-server"></a>建立控制項為 Automation 伺服器  
  
1.  [建立](../mfc/reference/mfc-activex-control-wizard.md)控制項。  
  
2.  [將方法加入](../mfc/mfc-activex-controls-methods.md)。  
  
3.  覆寫[IsInvokeAllowed](../mfc/reference/colecontrol-class.md#isinvokeallowed)。 如需詳細資訊，請參閱知識庫文章 Q146120。  
  
4.  建置控制項。  
  
### <a name="to-programmatically-access-the-methods-in-an-automation-server"></a>以程式設計方式存取 Automation 伺服器中的方法  
  
1.  建立應用程式，例如、 [MFC exe](../mfc/reference/mfc-application-wizard.md)。  
  
2.  在開頭`InitInstance`函式中，加入下列行：  
  
     [!code-cpp[NVC_MFC_AxCont#17](../mfc/codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_1.cpp)]  
  
3.  在 類別檢視，以滑鼠右鍵按一下專案節點，然後選取**從 typelib 加入類別**匯入類型程式庫。  
  
     這會將與檔案名稱副檔名.h 和.cpp 檔案加入專案。  
  
4.  標頭檔的類別，會呼叫一或多個方法，ActiveX 控制項中，加入下列行： `#include filename.h`，其中的檔案名稱是當您匯入類型程式庫已建立的標頭檔的名稱。  
  
5.  在 ActiveX 控制項中的方法會進行呼叫的函式，加入程式碼會建立控制項的包裝函式類別的物件，並建立 ActiveX 物件。 例如，下列的 MFC 程式碼會具現化`CCirc`控制項，取得 [標題] 屬性，並在對話方塊中按一下 [確定] 按鈕時顯示的結果：  
  
     [!code-cpp[NVC_MFC_AxCont#18](../mfc/codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_2.cpp)]  
  
 如果應用程式中使用後，您可以加入 ActiveX 控制項的方法，您可以開始在應用程式中使用控制項的最新版本，刪除您匯入類型程式庫時所建立的檔案。 然後再次匯入類型程式庫。  
  
## <a name="see-also"></a>另請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)

