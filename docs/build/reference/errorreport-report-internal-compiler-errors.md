---
title: /errorReport (回報編譯器內部錯誤)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.ErrorReporting
- /errorreport
helpviewer_keywords:
- /errorReport compiler option [C++]
- -errorReport compiler option [C++]
ms.assetid: 819828f8-b0a5-412c-9c57-bf822f17e667
ms.openlocfilehash: 8529e8c3cfc0914797c81207889a9505f1d57382
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660157"
---
# <a name="errorreport-report-internal-compiler-errors"></a>/errorReport (回報編譯器內部錯誤)

讓您可將內部編譯器錯誤 (ICE) 資訊直接提供給 Microsoft。

## <a name="syntax"></a>語法

```
/errorReport:[ none | prompt | queue | send ]
```

## <a name="arguments"></a>引數

**none**<br/>
將不會收集有關內部編譯器錯誤的報告，也不會將報告傳送給 Microsoft。

**提示**<br/>
提示您在收到內部編譯器錯誤時傳送報告。 **提示字元**是在開發環境中編譯應用程式的預設值。

**queue**<br/>
佇列錯誤報告。 當您登入系統管理員權限時，以便您可以報告自上次登入的任何失敗，會顯示的視窗 （您將不會提示您傳送錯誤報告的頻率超過每隔三天一次）。 **佇列**是應用程式會在命令提示字元進行編譯時的預設值。

**傳送**<br/>
如果將 Windows 錯誤報告的系統設定已啟用報告，會自動傳送給 Microsoft 報告內部編譯器錯誤。

## <a name="remarks"></a>備註

編譯器無法處理原始程式碼檔案時，就會出現編譯器內部錯誤 (ICE)。 發生 ICE 時，編譯器不會產生輸出檔或任何有用的診斷，無法讓您修正程式碼。

在舊版中，當您收到 ICE 時，我們鼓勵您連絡 Microsoft 產品支援服務回報問題。 具有 **/errorReport**，您可以直接向 Microsoft 提供 ICE 資訊。 您的錯誤報告有助於改善未來的編譯器版本。

使用者能否傳送報告，取決於電腦和使用者原則權限。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 **進階**屬性頁。

1. 修改**錯誤報告**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ErrorReporting%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)