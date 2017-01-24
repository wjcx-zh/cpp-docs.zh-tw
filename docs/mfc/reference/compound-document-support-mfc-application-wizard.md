---
title: "MFC 應用程式精靈、複合文件支援 | Microsoft Docs"
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
  - "vc.appwiz.mfc.exe.compdoc"
dev_langs: 
  - "C++"
ms.assetid: 42e1af83-12c4-438d-92eb-13835afdb148
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC 應用程式精靈、複合文件支援
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 MFC 應用程式精靈的這個頁面中，表示出應用程式可提供何種層級的複合及主動式文件支援。  您的應用程式必須支援文件 \/ 檢視架構，以支援複合文件和文件範本。  
  
 在預設情況下，應用程式不包含複合文件支援。  如果您接受這項預設，則應用程式無法支援主動式文件或複合檔案。  
  
 **複合文件支援**  
 判斷應用程式是否提供容器支援、伺服程式支援，或者兩者皆提供。  如需本範圍的詳細資訊，請參閱：  
  
-   [容器：容器的實作](../../mfc/containers-implementing-a-container.md)  
  
-   [伺服程式：實作一個伺服程式](../../mfc/servers-implementing-a-server.md)  
  
|選項|說明|  
|--------|--------|  
|**無**|表示不支援物件連結與內嵌 \(Object Linking and Embedding，OLE\)。  在預設情況下，應用程式精靈會在無 ActiveX 支援的情況下建立應用程式。|  
|**容器**|包含連結與內嵌物件。|  
|**迷你伺服程式**|表示應用程式可以建立和管理複合文件物件。  請注意，迷你伺服程式 \(Mini\-Server\) 無法單獨執行，同時僅支援內嵌項目。|  
|**全伺服程式**|表示應用程式可以建立和管理複合文件物件。  全伺服程式可單獨執行，並同時支援連結與內嵌項目。|  
|**容器\/全伺服程式**|表示應用程式可同時是容器和伺服程式。  容器是一種應用程式，可以將內嵌或連結項目加入到本身的文件中。  伺服程式是一種應用程式，可建立 Automation 項供容器應用程式使用。|  
  
 **其他選項**  
 指出應用程式是否支援主動式文件。  如需有關本功能的詳細資訊，請參閱[主動式文件](../../mfc/active-documents.md)。  
  
|選項|說明|  
|--------|--------|  
|**主動式文件伺服程式\(A\)**|表示應用程式可以建立和管理主動式文件。  如果選取本選項，則必須在精靈的[文件樣板字串](../../mfc/reference/document-template-strings-mfc-application-wizard.md)頁面中，於 \[副檔名\] 方塊內指定主動式文件伺服程式的副檔名。  如需詳細資訊，請參閱[主動式文件伺服程式](../../mfc/active-document-servers.md)。|  
|**主動式文件容器**|表示應用程式可於框架內包含主動式文件。  例如，主動式文件可能包括 Internet Explorer 文件、或者 Microsoft Word 檔案或 Excel 試算表等 Office 文件。  如需詳細資訊，請參閱 [主動式文件內含項目](../../mfc/active-document-containment.md)。|  
|**支援複合檔案\(U\)**|不使用複合檔案格式將容器應用程式的文件序列化。  本選項會強制將整個包含物件的檔案載入記憶體。  個別物件的累加儲存不適用。  如果某物件已變更並儲存，則檔案中所有物件皆會儲存。|  
  
## 請參閱  
 [MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)