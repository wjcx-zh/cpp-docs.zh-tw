---
title: "資源檔 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- resource files
- resources [C++]
- file types [C++], resource files
ms.assetid: 338a4a0f-0c62-4ef1-a34f-5d86262d93a4
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c674bc7711de8a7991ad6906d62a768f9360e6b8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="resource-files-c"></a>資源檔 (C++)
資源是提供資訊給使用者介面項目。 點陣圖、 圖示、 工具列和資料指標是所有資源。 某些資源都可以執行的動作，例如從功能表中選取或輸入 對話方塊中的資料操作。  
  
 請參閱[使用資源](../windows/working-with-resource-files.md)如需詳細資訊。  
  
|檔案名稱|目錄位置|方案總管位置|說明|  
|---------------|------------------------|--------------------------------|-----------------|  
|*Projname*.rc|*專案名稱*|原始程式檔|專案資源指令碼檔案。 資源指令碼檔包含下列項目，視專案，以及選取的專案 （例如工具列、 對話方塊或 HTML） 支援的類型而定：<br /><br /> 預設功能表定義中。<br />-快速鍵和字串資料表。<br />-預設**有關** 對話方塊。<br />-其他對話方塊。<br />圖示檔案 (res\\*Projname*.ico)。<br />版本資訊。<br />-點陣圖。<br />-工具列。<br />HTML 檔案。<br /><br /> 資源檔包含標準 Mfc 資源檔 Afxres.rc。|  
|偵錯工具|*專案名稱*|標頭檔|包含專案所使用的資源定義的資源標頭檔。|  
|*Projname*.rc2|*Projname*\res|原始程式檔|包含專案所使用的其他資源指令碼檔案。 您可以包含在專案的.rc 檔的頂端.rc2 檔。<br /><br /> .rc2 檔非常有用，包括數個不同的專案所使用的資源。 而不必建立數次為不同的專案相同的資源，您可以將它們放在.rc2 檔，並將.rc2 檔包含在主要.rc 檔。|  
|*Projname*.def|*專案名稱*|原始程式檔|DLL 專案的模組定義檔。 控制項，它會提供名稱和描述的控制項，以及執行階段堆積的大小。|  
|*Projname*.ico|*Projname*\res|資源檔|專案或控制項的圖示檔。 應用程式最小化時，會出現這個圖示。 它也會在應用程式的**有關**方塊。 根據預設，MFC 提供 MFC 圖示和 ATL 提供 ATL 圖示。|  
|*Projname*Doc.ico|*Projname*\res|資源檔|針對包含文件/檢視架構的支援的 MFC 專案圖示檔。|  
|Toolbar.bmp|*Projname*\res|資源檔|代表應用程式或工具列或調色盤中的控制項的點陣圖檔案。 此點陣圖會包含在專案的資源檔案。 初始的工具列和狀態列中建構**CMainFrame**類別。|  
|ribbon.mfcribbon ms|*Projname*\res|資源檔|資源檔，其中包含定義功能區按鈕、 控制項和屬性的 XML 程式碼。 如需詳細資訊，請參閱 [Ribbon Designer (MFC)](../mfc/ribbon-designer-mfc.md)。|  
  
## <a name="see-also"></a>另請參閱  
 [為 Visual C++ 專案建立的檔案類型](../ide/file-types-created-for-visual-cpp-projects.md)