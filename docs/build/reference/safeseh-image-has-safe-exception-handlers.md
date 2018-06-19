---
title: -/SAFESEH （影像擁有安全例外狀況處理常式） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /SAFESEH
dev_langs:
- C++
helpviewer_keywords:
- /SAFESEH linker option
- -SAFESEH linker option
- SAFESEH linker option
ms.assetid: 7722ff99-b833-4c65-a855-aaca902ffcb7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 54d13e6922650f0193d4bbc3469d4acf25904234
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377905"
---
# <a name="safeseh-image-has-safe-exception-handlers"></a>/SAFESEH (影像擁有安全例外狀況處理常式)
```  
/SAFESEH[:NO]  
```  
  
 當 **/SAFESEH**指定，則連結器只會產生一個映像，是否它也可以產生映像的安全例外狀況處理常式的表格。 此資料表會指定哪些例外狀況處理常式都適用於映像的作業系統。  
  
 **/SAFESEH**適用於 x86 連結時才有效目標。 **/SAFESEH**已經有註明的例外狀況處理常式的平台不支援。 例如，在 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 和 ARM 上，所有例外狀況處理常式都已在 PDATA 中註明。 ML64.exe 可支援將發出 SEH 資訊 （XDATA 和 PDATA） 的註解為映像，可讓您透過 ml64 函式回溯。 請參閱[MASM (ml64.exe) x64](../../assembler/masm/masm-for-x64-ml64-exe.md)如需詳細資訊。  
  
 如果 **/SAFESEH**未指定，如果所有模組都都與安全例外狀況處理功能相容，連結器會產生安全例外狀況處理常式的表格的映像。 如果任何模組不相容於安全例外狀況處理功能，產生的映像不會包含安全例外狀況處理常式的表格。 如果[/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) WINDOWSCE 或其中一個 EFI_ * 選項，指定連結器不會嘗試產生一個映像包含表格的安全例外狀況處理常式，兩者的那些子系統可以進行時使用的資訊。  
  
 如果 **/SAFESEH:NO**指定，則連結器不會產生安全例外狀況處理常式的表格的映像，即使所有模組都都與安全例外狀況處理功能相容。  
  
 連結器無法產生影像的最常見原因是因為一或多個連結器輸入檔 （模組） 無法與安全例外狀況處理常式的功能相容。 模組不相容於安全例外狀況處理常式的一個常見原因是因為它以舊版的 Visual c + + 編譯器建立。  
  
 您也可以註冊為結構化例外狀況處理常式函式，使用[。SAFESEH](../../assembler/masm/dot-safeseh.md)。  
  
 不可能將標示的現有二進位為具有安全例外狀況處理常式 （或任何例外狀況處理常式）。在建置階段，就必須加入安全例外狀況處理的詳細資訊。  
  
 建置安全例外狀況處理常式的表格的連結器的能力取決於使用 C 執行階段程式庫的應用程式。 如果連結[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)而且您想安全例外狀況處理常式的表格，您需要提供載入組態結構 （例如可以 loadcfg.c CRT 原始程式檔中找到），其中包含 Visual c + + 所定義的所有項目。 例如:   
  
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
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取**連結器**資料夾。  
  
3.  選取**命令列**屬性頁。  
  
4.  輸入到選項**其他選項**方塊。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)