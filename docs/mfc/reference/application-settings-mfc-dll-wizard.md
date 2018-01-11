---
title: "MFC DLL 精靈、 應用程式設定 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.mfc.dll.appset
dev_langs: C++
helpviewer_keywords: MFC DLL Wizard, application settings
ms.assetid: 0a96b94f-ae36-4975-951b-c9ffb3def21c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1851460d5cf9deb8a803b13ec75d92c45c03e607
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="application-settings-mfc-dll-wizard"></a>MFC DLL 精靈、應用程式設定
使用 MFC DLL 精靈的這個頁面來設計和加入新的 MFC DLL 專案的基本功能。  
  
## <a name="dll-type"></a>DLL 類型  
 選取您想要建立之 DLL 的類型。  
  
 **使用標準的 MFC DLL 共用 MFC DLL**  
 選取此選項即可連結 MFC 程式庫加入您的程式做為共用的 DLL。 使用此選項，您無法共用 MFC 物件 DLL 和程式之間呼叫的應用程式。 您的程式在執行階段會呼叫 MFC 程式庫。 如果它使用 MFC 程式庫的多個執行檔所組成，此選項可減少您的程式的磁碟和記憶體需求。 Win32 和 MFC 程式可以在 DLL 中呼叫函式。 您必須重新發佈此專案類型的 MFC DLL。  
  
 **以靜態方式連結 mfc 的標準 MFC DLL**  
 選取此選項即可在建置階段您的程式以靜態方式連結 MFC 程式庫。 Win32 和 MFC 程式可以在 DLL 中呼叫函式。 雖然此選項會增加程式的大小，您不需要轉散發 MFC DLL，這種類型的專案。 您無法在您的 DLL 和呼叫的應用程式之間共用 MFC 物件。  
  
 **MFC 擴充 DLL**  
 如果您要在執行階段，進行呼叫 MFC 程式庫程式，而且您想要共用您的 DLL 和呼叫的應用程式之間的 MFC 物件，請選取此選項。 如果它由所有使用 MFC 程式庫的多個可執行檔所組成，此選項可減少您的程式、 磁碟和記憶體需求。 只有 MFC 程式可以在 DLL 中呼叫函式。 您必須重新發佈此專案類型的 MFC DLL。  
  
## <a name="additional-features"></a>其他功能  
 選取是否 MFC DLL 應支援 automation，以及是否應支援 Windows sockets。  
  
 **Automation**  
 選取**自動化**允許您的程式操作另一個程式中實作的物件。 選取**自動化**也會公開您的程式，向其他自動化用戶端。 請參閱[自動化](../../mfc/automation.md)如需詳細資訊。  
  
 **Windows 通訊端**  
 選取此選項以指出您的程式支援 Windows sockets。 Windows 通訊端可以讓您撰寫的程式可透過 TCP/IP 網路通訊。  
  
 當您的 MFC DLL，與 Windows 通訊端會建立支援， [Afxenablecontrolcontainer](../../mfc/reference/cwinapp-class.md#initinstance)初始化支援的通訊端且 MFC 標頭檔 StdAfx.h 包含 AfxSock.h。  
  
## <a name="see-also"></a>請參閱  
 [MFC DLL 精靈](../../mfc/reference/mfc-dll-wizard.md)   
 [建立 MFC DLL 專案](../../mfc/reference/creating-an-mfc-dll-project.md)

