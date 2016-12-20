---
title: "MFC DLL 精靈、應用程式設定 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.mfc.dll.appset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC DLL 精靈, 應用程式設定"
ms.assetid: 0a96b94f-ae36-4975-951b-c9ffb3def21c
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC DLL 精靈、應用程式設定
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可使用 MFC DLL 精靈的這個頁面來設計基本功能並將其加入至新的 MFC DLL 專案中。  
  
## DLL 類型  
 選取要建立的 DLL 類型。  
  
 **使用共用 MFC DLL 的標準 DLL**  
 選取這個選項將 MFC 程式庫當做共用 DLL 連結至您的程式。  若使用這個選項，則 DLL 和呼叫的應用程式之間便無法共用 MFC 物件。  您的程式會在執行階段時呼叫 MFC 程式庫。  如果程式是由使用 MFC 程式庫的多個執行檔所組成，則這個選項能夠減少程式的磁碟和記憶體需求。  Win32 和 MFC 程式都能呼叫 DLL 中的函式。  您必須轉散發這種專案的 MFC DLL。  
  
 **MFC 靜態連結的標準 DLL**  
 選取這個選項可在建置階段將程式靜態連結至 MFC 程式庫。  Win32 和 MFC 程式都能呼叫 DLL 中的函式。  由於這個選項會增加程式的大小，因此您不需要轉散發這種專案的 MFC DLL。  您的 DLL 和呼叫的應用程式之間無法共用 MFC 物件。  
  
 **MFC 擴充 DLL**  
 如果要使程式在執行階段時呼叫 MFC 程式庫，且要讓 DLL 和呼叫的應用程式之間共用 MFC 物件，則請選取這個選項。  如果程式是由使用 MFC 程式庫的多個可執行檔組成，則這個選項能夠減少程式的磁碟和記憶體需求。  只有 MFC 程式能夠呼叫 DLL 中的函式。  您必須轉散發這種專案的 MFC DLL。  
  
## 其他功能  
 選取 MFC DLL 來得知是否應支援 Automation 以及是否應支援 Windows Sockets。  
  
 **Automation**  
 選取 **Automation** 來允許程式操作其他程式實作的物件。  選取 **Automation** 也會將您的程式公開給其他 Automation 用戶端。  如需詳細資訊，請參閱 [Automation](../../mfc/automation.md)。  
  
 **Windows Sockets**  
 選取這個選項來指出程式是否支援 Windows Sockets。  Windows Sockets 允許您撰寫在 TCP\/IP 網路上通訊的程式。  
  
 當您建立可支援 Windows Sockets 的 MFC DLL 時，[CWinApp::InitInstance](../Topic/CWinApp::InitInstance.md) 會初始化通訊端的支援，同時 MFC 標頭檔 StdAfx.h 會包含 AfxSock.h。  
  
## 請參閱  
 [MFC DLL 精靈](../../mfc/reference/mfc-dll-wizard.md)   
 [建立 MFC DLL 專案](../../mfc/reference/creating-an-mfc-dll-project.md)