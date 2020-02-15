---
title: /ERRORREPORT (回報內部連結器錯誤)
description: Microsoft NMAKE 命令列選項的參考指南。
ms.date: 02/09/2020
f1_keywords:
- /ERRORREPORT
- VC.Project.VCLinkerTool.ErrorReporting
helpviewer_keywords:
- /ERRORREPORT linker option
- ERRORREPORT linker option
- -ERRORREPORT linker option
ms.assetid: f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28
ms.openlocfilehash: 5e919d4f7eb59524b9145c8e3e59613e60aef1d2
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257685"
---
# <a name="errorreport-report-internal-linker-errors"></a>/ERRORREPORT (回報內部連結器錯誤)

**/ERRORREPORT**選項已被取代。 從 Windows Vista 開始，錯誤報表是由[Windows 錯誤報告（WER）](/windows/win32/wer/windows-error-reporting)設定所控制。

## <a name="syntax"></a>語法

> **/ERRORREPORT：** \[ **none** \|**提示**字元 \|**佇列**\|**傳送**]

## <a name="remarks"></a>備註

Windows 錯誤報告的服務設定會覆寫 **/ERRORREPORT**引數。 如果 Windows 錯誤報告啟用報告功能，則連結器會自動將內部錯誤的報告傳送給 Microsoft。 如果 Windows 錯誤報告停用，則不會傳送任何報表。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 開啟 [設定**屬性**] > **連結器** > [ **Advanced** ] 屬性頁。

1. 修改 [**錯誤報表**] 屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ErrorReporting%2A>＞。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)\
[MSVC 連結器選項](linker-options.md)
