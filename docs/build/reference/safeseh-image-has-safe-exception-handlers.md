---
title: "/SAFESEH (影像擁有安全例外狀況處理常式) | Microsoft Docs"
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
  - "/SAFESEH"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/SAFESEH 連結器選項"
  - "-SAFESEH 連結器選項"
  - "SAFESEH 連結器選項"
ms.assetid: 7722ff99-b833-4c65-a855-aaca902ffcb7
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /SAFESEH (影像擁有安全例外狀況處理常式)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/SAFESEH[:NO]  
```  
  
 指定 **\/SAFESEH** 時，若連結器也可產生影像安全例外狀況處理常式的表格，將只會產生一個影像。  這個表格會告訴作業系統，哪個例外狀況處理常式對映像有效。  
  
 **\/SAFESEH** 只有在連結 x86 目標時才有效。  **\/SAFESEH** 在已經註明有例外狀況處理常式的平台上不支援 。  例如，在 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 和 ARM 上，所有例外狀況處理常式都已在 PDATA 中註明。  ML64.exe 有支援可加入發出 SEH 資訊 \(XDATA 和 PDATA\) 至影像的附註，可以讓您一直回溯到 ml64 函式。  如需詳細資訊，請參閱[MASM for x64 \(ml64.exe\)](../../assembler/masm/masm-for-x64-ml64-exe.md)。  
  
 若未指定 **\/SAFESEH**，則在所有模組都與安全例外狀況處理功能相容時，連結器將會產生包含安全例外狀況處理常式表格的影像。  若有任何模組與安全例外狀況處理功能不相容，產生的影像將不包含安全例外狀況處理常式的表格。  若 [\/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) 指定 WINDOWSCE 或某個 EFI\_\* 選項，連結器將不會嘗試產生包含安全例外狀況處理常式表格的影像，因為這些子系統都不會使用該資訊。  
  
 若已指定 **\/SAFESEH:NO**，即使所有模組都能與安全例外狀況處理功能相容，連結器也不會產生包含安全例外狀況處理常式表格的影像。  
  
 連結器無法產生影像最常見的原因，是連結器的一個或多個輸入檔 \(模組\) 與安全例外狀況處理常式功能不相容。  模組與安全例外狀況處理常式不相容的原因，通常是因為它是以舊版的 Visual C\+\+ 編譯器建立的。  
  
 您也可以透過使用 [.SAFESEH](../../assembler/masm/dot-safeseh.md)，將函式註冊為結構化例外狀況處理常式。  
  
 現有的二進位都無法標示為有安全例外狀況處理常式 \(或沒有例外狀況處理常式\)；安全例外狀況處理的相關資訊都必須在建置階段加入。  
  
 連結器建置安全例外狀況處理常式表格的能力，是取決於使用 C Runtime 程式庫的應用程式。  若您以 [\/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) 連結，並且需要安全例外狀況處理常式的表格，就需要提供載入組態結構 \(例如在 loadcfg.c CRT 原始程式檔內可發現的載入組態結構\)，其中包含針對 Visual C\+\+ 定義的所有項目。  例如：  
  
```  
#include <windows.h>  
extern DWORD_PTR __security_cookie;  /* /GS security cookie */  
  
/*  
 * The following two names are automatically created by the linker for any  
 * image that has the safe exception table present.  
*/  
  
extern PVOID __safe_se_handler_table[]; /* base of safe handler entry table */  
extern BYTE  __safe_se_handler_count;  /* absolute symbol whose address is  
                                           the count of table entries */  
typedef struct {  
    DWORD       Size;  
    DWORD       TimeDateStamp;  
    WORD        MajorVersion;  
    WORD        MinorVersion;  
    DWORD       GlobalFlagsClear;  
    DWORD       GlobalFlagsSet;  
    DWORD       CriticalSectionDefaultTimeout;  
    DWORD       DeCommitFreeBlockThreshold;  
    DWORD       DeCommitTotalFreeThreshold;  
    DWORD       LockPrefixTable;            // VA  
    DWORD       MaximumAllocationSize;  
    DWORD       VirtualMemoryThreshold;  
    DWORD       ProcessHeapFlags;  
    DWORD       ProcessAffinityMask;  
    WORD        CSDVersion;  
    WORD        Reserved1;  
    DWORD       EditList;                   // VA  
    DWORD_PTR   *SecurityCookie;  
    PVOID       *SEHandlerTable;  
    DWORD       SEHandlerCount;  
} IMAGE_LOAD_CONFIG_DIRECTORY32_2;  
  
const IMAGE_LOAD_CONFIG_DIRECTORY32_2 _load_config_used = {  
    sizeof(IMAGE_LOAD_CONFIG_DIRECTORY32_2),  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    &__security_cookie,  
    __safe_se_handler_table,  
    (DWORD)(DWORD_PTR) &__safe_se_handler_count  
};  
```  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取 \[**連結器**\] 資料夾。  
  
3.  選取 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中輸入選項。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)