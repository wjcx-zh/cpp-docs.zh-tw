---
title: "如何：從現有的 .ctc 檔建立 .vsct 檔 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT 檔案, 根據 .ctc 檔建立"
ms.assetid: 700e80a4-c1e1-4178-af53-45e86dd2c08b
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# 如何：從現有的 .ctc 檔建立 .vsct 檔
您可以從現有命令資料表 .ctc 原始程式檔建立 XML .vsct 檔。 這樣做，您可以充分利用新的 XML [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 命令資料表 \(VSCT\) 編譯器格式。  
  
### 從 .ctc 檔建立 .vsct 檔  
  
1.  取得一份 Perl 語言。  
  
2.  取得一份 Perl 指令碼 ConvertCTCToVSCT.pl，一般位於 *\<Visual Studio SDK 安裝路徑\>*\\VisualStudioIntegration\\Tools\\bin 資料夾中。  
  
3.  取得一份您想要轉換的 .ctc 原始程式檔。  
  
4.  將檔案放置在相同的目錄中。  
  
5.  在 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] \[命令提示字元\] 視窗中，巡覽至該目錄。  
  
6.  類型  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     其中，PkgCmd.ctc 是 .ctc 檔的名稱，而 PkgCmd.vsct 是您要建立之 vsct 檔的名稱。  
  
     這會建立新的 .vsct XML 命令資料表原始程式檔。 您可以像是處理任何其他 .vsct 檔一樣，使用 Vsct.exe \(VSCT 編譯器\) 編譯此檔案。  
  
    > [!NOTE]
    >  您可以重新格式化 XML 註解來改善 .vsct 檔的可讀性。  
  
## 請參閱  
 [如何: 建立。Vsct 檔案](../Topic/How%20to:%20Create%20a%20.Vsct%20File.md)   
 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../Topic/Visual%20Studio%20Command%20Table%20\(.Vsct\)%20Files.md)