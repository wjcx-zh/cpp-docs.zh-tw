---
title: /ERRORREPORT (回報內部連結器錯誤)
description: 瞭解如何使用/ERRORREPORT。
ms.date: 02/09/2020
f1_keywords:
- /ERRORREPORT
- VC.Project.VCLinkerTool.ErrorReporting
helpviewer_keywords:
- /ERRORREPORT linker option
- ERRORREPORT linker option
- -ERRORREPORT linker option
ms.assetid: f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28
ms.openlocfilehash: 7d16904da8490018235278347f23e37339739415
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742732"
---
# <a name="errorreport-report-internal-linker-errors"></a>/ERRORREPORT (回報內部連結器錯誤)

**/ERRORREPORT**選項已被取代。 從 Windows Vista 開始，錯誤報表是由 [Windows 錯誤報告 (WER) ](/windows/win32/wer/windows-error-reporting) 設定來控制。

## <a name="syntax"></a>語法

> **/ERRORREPORT：** \[**無** \|**提示** \|**佇列** \|**傳送**]

## <a name="remarks"></a>備註

**/ERRORREPORT**引數會由 Windows 錯誤報告服務設定覆寫。 如果 Windows 錯誤報告啟用報告功能，連結器會自動將內部錯誤的報告傳送給 Microsoft。 如果 Windows 錯誤報告停用，就不會傳送任何報告。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 開啟設定**屬性**  >  **連結器**的 [  >  **Advanced** ] 屬性頁。

1. 修改 **錯誤報表** 屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ErrorReporting%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)\
[MSVC 連結器選項](linker-options.md)
