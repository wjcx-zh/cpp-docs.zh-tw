---
title: "/INTEGRITYCHECK (需要簽章檢查) | Microsoft Docs"
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
ms.assetid: 9e738825-2c98-40cd-8ad2-5d0d9c14893e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /INTEGRITYCHECK (需要簽章檢查)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定必須在載入期間檢查二進位檔映像的數位簽章。  
  
```  
/INTEGRITYCHECK[:NO]  
```  
  
## 備註  
 根據預設值，**\/INTEGRITYCHECK** 為 off。  
  
 在 DLL 或可執行檔的 PE 標頭中，**\/INTEGRITYCHECK** 選項會設定旗標，要求記憶體管理員檢查數位簽章，以便將影像載入 Windows 中。  這個選項必須設成32位元和64位元皆可實作特定 Windows 功能載入的核心模式程式碼的 DDL ，而且建議 Windows Vista、 [!INCLUDE[win7](../../build/includes/win7_md.md)]、[!INCLUDE[win8](../../build/includes/win8_md.md)]、[!INCLUDE[winsvr08](../../build/includes/winsvr08_md.md)]和[!INCLUDE[winserver8](../../build/includes/winserver8_md.md)] 使用這個選項。  Windows Vista 之前的 Windows 版本會忽略這個旗標。  如需詳細資訊，請參閱[可攜式執行檔 \(PE\) 的強制完整性簽署](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx) \(英文\)。  
  
### 在 Visual Studio 中設定這個連結器選項  
  
1.  開啟專案 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展開 \[**組態屬性**\] 節點。  
  
3.  展開 **\[連結器\]** 節點。  
  
4.  選取 \[**命令列**\] 屬性頁。  
  
5.  在 \[**其他選項**\] 中，輸入 `/INTEGRITYCHECK` 或 `/INTEGRITYCHECK:NO`。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)   
 [可攜式執行檔 \(PE\) 的強制完整性簽署](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)   
 [核心模式程式碼簽署逐步解說](http://msdn.microsoft.com/windows/hardware/gg487328.aspx)   
 [Windows 7 和 Windows Server 2008 中的 AppInit DLL](http://msdn.microsoft.com/windows/hardware/gg463040.aspx)