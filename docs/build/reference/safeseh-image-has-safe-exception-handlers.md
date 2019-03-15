---
title: /SAFESEH (影像擁有安全例外狀況處理常式)
ms.date: 11/04/2016
f1_keywords:
- /SAFESEH
helpviewer_keywords:
- /SAFESEH linker option
- -SAFESEH linker option
- SAFESEH linker option
ms.assetid: 7722ff99-b833-4c65-a855-aaca902ffcb7
ms.openlocfilehash: 62784933cbecd4f312c52ae98cab7d232b893f35
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822336"
---
# <a name="safeseh-image-has-safe-exception-handlers"></a>/SAFESEH (影像擁有安全例外狀況處理常式)

```
/SAFESEH[:NO]
```

當 **/SAFESEH**指定，連結器只會產生映像，是否它也可以產生映像的安全例外狀況處理常式的表格。 此資料表指定哪些例外狀況處理常式是有效的映像的作業系統。

**/SAFESEH**適用於 x86 連結時才有效目標。 **/SAFESEH**已經註明的例外狀況處理常式的平台不支援。 例如，在 x64 和 ARM 上，所有的例外狀況處理常式會註明在 PDATA 中。 ML64.exe 到映像，可讓您回溯透過 ml64 函式已加入發出 SEH 資訊 （XDATA 和 PDATA） 的註釋的支援。 請參閱[MASM (ml64.exe) x64 的](../../assembler/masm/masm-for-x64-ml64-exe.md)如需詳細資訊。

如果 **/SAFESEH**未指定，連結器將會產生安全的例外狀況處理常式的表格的映像，如果所有模組都都與安全例外狀況處理功能相容。 如果任何模組不相容於安全例外狀況處理功能，產生的映像將不會包含安全例外狀況處理常式的表格。 如果[/SUBSYSTEM](subsystem-specify-subsystem.md) WINDOWSCE 或其中一個 EFI_ * 選項，指定連結器不會嘗試產生映像包含表格的安全例外狀況處理常式，當兩者皆非的那些子系統可以使用的資訊。

如果 **/SAFESEH:NO**指定，連結器不會產生安全的例外狀況處理常式的表格的映像，即使所有模組都都與安全的例外狀況處理功能相容。

連結器不會產生映像的最常見原因是因為一或多個輸入檔案 （模組） 連結器無法與安全例外狀況處理常式的功能相容。 模組不相容於安全例外狀況處理常式的常見原因是因為它使用舊版 Visual c + + 編譯器建立。

您也可以註冊為結構化例外狀況處理常式函式，使用[。SAFESEH](../../assembler/masm/dot-safeseh.md)。

不可能將標示的現有二進位為有安全例外狀況處理常式 （或任何例外狀況處理常式）;必須在建置階段新增安全的例外狀況處理的詳細資訊。

建置安全的例外狀況處理常式的表格連結器的能力取決於使用 C 執行階段程式庫的應用程式。 如果連結[/NODEFAULTLIB](nodefaultlib-ignore-libraries.md)和您想要的安全例外狀況處理常式的資料表，您必須提供載入的組態結構 （例如可以 loadcfg.c CRT 原始程式檔中找到），其中包含 Visual c + + 定義的所有項目。 例如: 

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

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 **連結器**資料夾。

1. 選取 **命令列**屬性頁。

1. 輸入到選項**其他選項** 方塊中。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
