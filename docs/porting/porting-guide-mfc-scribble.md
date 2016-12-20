---
title: "移植指南：MFC Scribble | Microsoft Docs"
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
ms.assetid: 8ddb517d-89ba-41a1-ab0d-4d2c6d9047e8
caps.latest.revision: 5
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 移植指南：MFC Scribble
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題是介紹 Visual C\+\+ 專案升級程序之幾個主題中的第一個主題，該程序會將在舊版 Visual Studio 中建立的專案升級至 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)]。  這些主題以範例來介紹升級程序，從一個很簡單的專案開始，再移到稍微更複雜的專案。  在本主題中，我們將討論特定專案 MFC Scribble 的升級程序。  它很適合做為 C\+\+ 專案升級程序的基本入門。  
  
 Visual Studio 的每個版本都可能引入不相容的問題，而使得將程式碼從舊版 Visual Studio 移到新版 Visual Studio 的作業變得很複雜。  您有時需要在程式碼中進行變更，因此必須重新編譯和更新程式碼；有時則需要對專案檔進行變更。  當您開啟使用舊版 Visual Studio 建立的專案時，Visual Studio 會自動詢問您是否要將專案或方案更新為最新版本。  這些工具通常只會升級專案檔，而不會修改您的原始程式碼。  
  
## MFC Scribble  
 MFC Scribble 是已知隨附於許多不同 Visual C\+\+ 版本的範例。  它是簡單的繪圖應用程式，可繪製 MFC 的一些基本功能。  目前可用的版本有許多種，包括 Managed 程式碼和機器碼版本。  針對這個範例，我們找到使用 Visual Studio 2005 機器碼撰寫的舊版 Scribble，並在 [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] 中加以開啟。  
  
 嘗試升級之前，我們會先備份整個方案及其所有內容。  接著，我們需要決定升級的特定方法。  針對長時間未升級的較複雜方案和專案，您應該考慮一次升級一個 Visual Studio 版本。  如此一來，您可以縮小哪個版本的 Visual Studio 會引發問題。  針對簡單的專案，您可以先嘗試在最新版 Visual Studio 中開啟專案，並讓精靈轉換專案。  如果不行，您可以在擁有適當版本 Visual Studio 的存取權時，嘗試一次升級一個版本。  
  
 請注意，您也可以在命令列執行 devenv 並使用 `/Upgrade` 選項，而不使用精靈來升級專案。  請參閱 [\/Upgrade](../Topic/-Upgrade%20\(devenv.exe\).md)。  這對自動化大量專案的升級程序會很有幫助。  
  
### 步驟 1：轉換專案檔  
 當您在 Visual Studio 2015 中開啟舊專案檔時，Visual Studio 會詢問您是否要將專案檔轉換成最新版本，我們選擇接受，  接著會出現下列對話方塊：  
  
 ![檢閱專案和方案變更](../porting/media/scribbleprojectupgrade.png "ScribbleProjectUpgrade")  
  
 出現錯誤，通知我們 Itanium 目標無法使用，因此將不會進行轉換。  
  
  **專案遺漏了平台 'Itanium'。  將忽略本平台專用的所有組態及其檔案組態設定。  如果您希望此平台被轉換，請確定您已在 '%vctargetpath%\\platforms\\Itanium' 底下安裝對應的平台。  繼續在沒有此平台的情況下轉換本專案嗎？**  當這個舊版 Scribble 專案建立時，Itanium 是重要的目標平台。  Windows 平台不再支援 Itanium，因此我們選擇繼續而不支援 Itanium 平台。  
  
 Visual Studio 接著會顯示移轉報告，列出舊專案檔的所有問題。  
  
 ![升級報表](../porting/media/scribblemigrationreport.png "ScribbleMigrationReport")  
  
 在本例中，問題全部都是警告，而且 Visual Studio 已對專案檔進行適當的變更。  對於專案而言，最大的差異是建置工具從 vcbuild 變更為 msbuild。  這項變更最初是由 Visual Studio 2010 所引進。  其他變更還包括專案檔本身中項目順序的一些重新排列。  對於這個範例專案而言，這些問題都不需要進一步注意。  
  
### 步驟 2：建置專案  
 建置前，我們會先檢查平台工具組，以了解專案系統正在使用的編譯器版本。  在專案屬性對話方塊中，於 \[組態屬性\] 下的 \[一般\] 分類中，查看 \[平台工具組\] 屬性。  該屬性包含 Visual Studio 的版本和平台工具版本號碼，在本例中為 v140，代表 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 版的工具。  當您轉換原本使用 Visual C\+\+ 2010、2012 或 2013 編譯的專案時，工具組不會自動更新為 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 工具組。  在 Scribble 的案例中，我們轉換的版本是針對 Visual Studio 2005 所建立，因此會轉換為使用最新工具組。  
  
 建置時，第一個出現的問題與 MBCS 程式碼有關。  
  
  **錯誤 MSB8031:**  錯誤訊息中的連結會帶我們前往 Visual Studio 2013 中 MBCS 取代的相關主題。  Visual C\+\+ 2013 中的 MFC 安裝預設不包含 MFC 的 MBCS 版本。  需要有 MFC 的 MBCS 版本，才能以其目前格式建置這個專案。  我們可以移轉程式碼以使用 Unicode，或者下載並安裝 MFC 的 MBCS 版本。  如果選擇下載 MFC 的 MBCS 版本，則可以加入巨集 NO\_WARN\_MBCS\_MFC\_DEPRECATION 的定義，以隱藏這個警告。  
  
 若要下載 MFC 的 MBCS 版本，請先閱讀 [MFC MBCS DLL 附加元件](../mfc/mfc-mbcs-dll-add-on.md)一文和 VC 部落格中有關 MFC 的 MBCS 版本取代的資訊，並從[這裡](http://www.microsoft.com/download/details.aspx?id=44930)下載 MFC 的 MBCS 版本。  在專案屬性對話方塊中，於 \[C\/C\+\+\] 分類的 \[前置處理器\] 下，將 NO\_WARN\_MBCS\_MFC\_DEPRECATION 加入預先定義的巨集清單。  
  
 若要切換為 Unicode，請開啟專案的屬性，選擇 \[組態屬性\] 下的 \[一般\] 區段，然後尋找 \[字元集\] 屬性。  將這個屬性從 \[使用多位元組字元集\] 變更為 \[使用 Unicode 字元集\]。  這項變更的影響是，現在 \_UNICODE 和 UNICODE 巨集已定義，而 \_MBCS 未定義；您可以在屬性對話方塊 \[C\/C\+\+\] 分類下的 \[命令列\] 屬性中，進行確認。  
  
  **\/GS \/analyze\- \/W4 \/Gy \/Zc:wchar\_t \/Zi \/Gm\- \/O2 \/Ob1 \/Fd".  \\Release\\vc140.pdb" \/Zc:inline \/fp:precise \/D "\_AFXDLL" \/D "WIN32" \/D "NDEBUG" \/D "\_WINDOWS" \/D "\_UNICODE" \/D "UNICODE" \/errorReport:prompt \/GF \/WX \/Zc:forScope \/Gd \/Oy \/MD \/Fa".  \\Release\\" \/EHsc \/nologo \/Fo".  \\Release\\" \/Fp".  \\Release\\Scribble.pch"**  雖然 Scribble 專案未設定為使用 Unicode 字元進行編譯，但已使用 TCHAR \(而不是 char\) 撰寫，因此實際上不需要變更。  使用 Unicode 字元集的專案建置成功。  
  
 不過，還有另一個問題。  編譯器通知我們 \_WINNT32\_WINNT 未定義：  
  
  **\_WIN32\_WINNT 未定義。  預設為 \_WIN32\_WINNT\_MAXVER \(請參閱 WinSDKVer.h\)**  這是警告，而不是錯誤，而且在升級 Visual C\+\+ 專案時很常見。  這是定義將用來執行應用程式之最低 Windows 版本的巨集。  如果我們忽略這個警告，則表示接受預設值 \_WIN32\_WINNT\_MAXVER \(即目前的 Windows 版本\)。  如需可能值的列表，請參閱[使用 Windows 標頭](https://msdn.microsoft.com/en-us/library/aa383745.aspx)。  例如，我們可以將其設定為在 Vista 以後的任何版本上執行。  
  
```  
#define _WIN32_WINNT _WIN32_WINNT_VISTA  
```  
  
 如果程式碼使用的部分 Windows API 無法用於您以這個巨集指定的 Windows 版本，您應該會看到編譯器錯誤。  在 Scribble 程式碼的案例中，沒有任何錯誤。  
  
### 步驟 3：測試和偵錯  
 沒有測試套件，因此我們將直接啟動應用程式，並手動透過 UI 測試其功能。  未發現任何問題。  
  
### 步驟 4：改良程式碼  
 移轉至 Visual Studio 2015 之後，您可能想要進行一些變更，以利用新的 C\+\+ 功能。  Visual C\+\+ 編譯器的目前版本比較符合 C\+\+ 標準，因此如果您想要對程式碼做一些變更，讓程式碼更安全且更容易移植到其他編譯器和作業系統，您應該考慮進行一些改良。  
  
## 後續步驟  
 Scribble 是小型且簡單的 Windows 桌面應用程式，並不難轉換。  許多小型、簡單的應用程式也同樣容易轉換至新版。  至於較複雜的應用程式 \(具有更多行程式碼、可能不及最新工程標準的舊版程式碼、多個專案和程式庫、自訂建置步驟\)，或複雜的指令碼式自動化組建，則需要更多時間進行升級。  請繼續進行[下一個範例](../porting/porting-guide-com-spy.md)：一個稱為 COM Spy 的 ATL\/COM 應用程式。  
  
## 請參閱  
 [移植和升級：範例和案例研究](../porting/porting-and-upgrading-examples-and-case-studies.md)   
 [下一個範例：COM Spy](../porting/porting-guide-com-spy.md)