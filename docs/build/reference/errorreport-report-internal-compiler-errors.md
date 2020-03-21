---
title: /errorReport (回報編譯器內部錯誤)
description: Microsoft C/C++編譯器/errorReport 命令列選項的參考。
ms.date: 02/09/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.ErrorReporting
helpviewer_keywords:
- /errorReport compiler option [C++]
- -errorReport compiler option [C++]
ms.assetid: 819828f8-b0a5-412c-9c57-bf822f17e667
ms.openlocfilehash: 9efe96ed2611795e1fef408ad07b49d65261c3b1
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075089"
---
# <a name="errorreport-report-internal-compiler-errors"></a>/errorReport (回報編譯器內部錯誤)

> [!NOTE]
> **/ErrorReport**選項已被取代。 從 Windows Vista 開始，錯誤報表是由[Windows 錯誤報告（WER）](/windows/win32/wer/windows-error-reporting)設定所控制。

## <a name="syntax"></a>語法

> **/errorReport：** \[**none** \|**提示**字元 \|**佇列**\|**傳送**]

## <a name="remarks"></a>備註

編譯器無法處理原始程式碼檔案時，會產生內部編譯器錯誤（ICE）。 當 ICE 發生時，編譯器不會產生輸出檔，或任何可用來修正程式碼的實用診斷。

Windows 錯誤報告的服務設定會覆寫 **/errorReport**引數。 如果 Windows 錯誤報告啟用報告功能，編譯器會自動將內部錯誤的報告傳送給 Microsoft。 如果 Windows 錯誤報告停用，則不會傳送任何報表。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 開啟 [設定**屬性**] > [ **C/C++**  > **Advanced** ] 屬性頁。

1. 修改 [**錯誤報表**] 屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ErrorReporting%2A>＞。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)\
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
