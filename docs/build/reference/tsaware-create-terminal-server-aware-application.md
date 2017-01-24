---
title: "/TSAWARE (建立終端伺服器感知應用程式) | Microsoft Docs"
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
  - "/tsaware"
  - "VC.Project.VCLinkerTool.TerminalServerAware"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/TSAWARE 連結器選項"
  - "終端伺服器"
  - "終端伺服器, 終端伺服器感知應用程式"
  - "TSAWARE 連結器選項"
  - "-TSAWARE 連結器選項"
ms.assetid: fe1c1846-de5b-4839-b562-93fbfe36cd29
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /TSAWARE (建立終端伺服器感知應用程式)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/TSAWARE[:NO]  
```  
  
## 備註  
 \/TSAWARE 選項會在程式映像的選擇性標頭的 IMAGE\_OPTIONAL\_HEADER DllCharacteristics 欄位中設定一個旗標。  當設定這個旗標後，終端伺服器將不會對應用程式進行某些變更。  
  
 如果應用程式不是終端伺服器感知 \(也稱為舊版應用程式\)，終端伺服器便會對這個舊版應用程式進行某些修改，使它能在多使用者環境中正確地運作。  例如，終端伺服器將會建立一個虛擬 Windows 資料夾，使得每位使用者都能取得一個 Windows 資料夾，而不是取得系統的 Windows 目錄。  這樣就可以讓使用者都能存取自己的 INI 檔。  此外，終端伺服器對於舊版應用程式的登錄也會進行一些調整，  這些修改會使得舊版應用程式在終端伺服器上的載入速度變慢。  
  
 如果應用程式為終端伺服器感知，它在安裝過程中必須不使用 INI 檔也不寫入 **HKEY\_CURRENT\_USER** 登錄。  
  
 如果您使用了 \/TSAWARE 而且您的應用程式仍然要使用 INI 檔，那麼這些檔案將會被系統上的所有使用者共用。  如果這種情況是可以接受，那麼您仍然可以使用 \/TSAWARE 以連結應用程式，否則，您必須使用 \/TSAWARE:NO。  
  
 對 Windows 和主控台應用程式而言，\/TSAWARE 選項對 Windows 2000 以及更新版本預設為啟用。  如需詳細資訊，請參閱 [\/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) 和 [\/VERSION](../../build/reference/version-version-information.md)。  
  
 \/TSAWARE 對於驅動程式、VxD 或 DLL 而言是為無效的。  
  
 如果應用程式是以 \/TSAWARE 連結的，DUMPBIN [\/HEADERS](../../build/reference/headers.md) 將會顯示此一效果的資訊。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[系統\] 屬性頁。  
  
4.  修改 \[終端伺服器\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TerminalServerAware%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)   
 [Storing User\-Specific Information](http://msdn.microsoft.com/library/aa383452)   
 [Legacy Applications in a Terminal Services Environment](https://msdn.microsoft.com/en-us/library/aa382957.aspx)