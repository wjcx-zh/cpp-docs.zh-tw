---
title: "/APPCONTAINER (Windows 市集應用程式) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 9a432db5-7640-460b-ab18-6f61fa7daf6f
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /APPCONTAINER (Windows 市集應用程式)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定連結器是否建立必須在應用程式容器中執行的可執行檔映像。  
  
## 語法  
  
```  
/APPCONTAINER[:NO]  
```  
  
## 備註  
 \/APPCONTAINER 預設為關閉。  
  
 這個選項會修改可執行檔，指示是否必須在 appcontainer 處理序隔離環境中執行應用程式。  為必須在 appcontainer 環境中執行的應用程式 \(例如 [!INCLUDE[win8_appstore_long](../../build/reference/includes/win8_appstore_long_md.md)]應用程式\)，指定 \/APPCONTAINER。\(當您從範本建立 [!INCLUDE[win8_appstore_long](../../build/reference/includes/win8_appstore_long_md.md)] 應用程式時，Visual Studio 會自動設定此選項\)。對於桌面應用程式，指定 \/APPCONTAINER:NO 或省略選項。  
  
 \/APPCONTAINER 選項是 [!INCLUDE[win8](../../build/includes/win8_md.md)] 引入的。  
  
### 在 Visual Studio 中設定這個連結器選項  
  
1.  開啟專案 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展開 \[**組態屬性**\] 節點。  
  
3.  展開 **\[連結器\]** 節點。  
  
4.  選取 \[**命令列**\] 屬性頁。  
  
5.  在 \[**其他選項**\] 中，輸入 `/APPCONTAINER` 或 `/APPCONTAINER:NO`。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)