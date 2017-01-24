---
title: "/FS (強制同步 PDB 寫入) | Microsoft Docs"
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
  - "/FS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "-FS 編譯器選項 [C++]"
  - "/FS 編譯器選項 [C++]"
ms.assetid: b2caaffe-f6e1-4963-b068-648f06b105e0
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /FS (強制同步 PDB 寫入)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

強制寫入要透過 MSPDBSRV.EXE 序列化的\(由[\/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) or [\/ZI](../../build/reference/z7-zi-zi-debug-information-format.md)產生的\)程式資料庫 \(PDB\) 檔案。  
  
## 語法  
  
```  
/FS  
```  
  
## 備註  
 根據預設，當 **\/Zi** ，或 **\/ZI** 指定時，編譯器會鎖定 PDB 檔案寫入型別資訊和符號偵錯資訊。  當型別數目很大時這可以大幅降低它採用編譯器會產生型別資訊的時間。  如果另一處理序暫時鎖定 PDB 檔案 \(例如，防毒程式\)由編譯器的寫入可能會失敗，而嚴重錯誤可能會發生。  這個問題也可能會發生在 cl.exe 多份存取同一個 PDB 檔 \(例如，如果方案有獨立使用相同的中繼目錄或輸出目錄和平行建置的專案已啟用\)。  將存取**\/FS** 編譯器選項防止編譯器鎖定 PDB 檔案並強制寫入通過 MSPDBSRV.EXE。  這可能會使組建所著更長，而當 cl.exe 多執行個體同時存取 PDB 檔案它不能避免可能發生的任何錯誤。  建議您變更方案，以便獨立專案寫入分隔中繼檔和輸出位置，或者您將專案相依於另一端以強制序列化的專案。  
  
 預設 [\/MP](../../build/reference/mp-build-with-multiple-processes.md) 選項啟用 **\/FS** 。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取 \[**C\/C\+\+**\] 資料夾。  
  
3.  選取 \[**命令列**\] 屬性頁。  
  
4.  修改 \[**其他選項**\] 屬性以包含 `/FS`，然後選擇 \[**確定**\]。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)