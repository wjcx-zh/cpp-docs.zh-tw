---
title: /execution-charset (設定執行字元集)
ms.date: 02/06/2019
f1_keywords:
- execution-charset
- /execution-charset
helpviewer_keywords:
- /execution-charset compiler option
- -execution-charset compiler option
ms.assetid: 0e02f487-2236-45bc-95f3-5760933a8f96
ms.openlocfilehash: 44e83524867bc8a914706e1f5b45b61bc4a48087
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492908"
---
# <a name="execution-charset-set-execution-character-set"></a>/execution-charset (設定執行字元集)

可讓您指定可執行檔的執行字元集。

## <a name="syntax"></a>語法

```
/execution-charset:[IANA_name|.CPID]
```

## <a name="arguments"></a>引數

*IANA_name*<br/>
IANA 定義的字元集名稱。

*CPID*<br/>
字碼頁識別碼。

## <a name="remarks"></a>備註

您可以使用 **/execution-charset**選項來指定執行字元集。 執行字元集是在所有前置處理步驟之後, 針對編譯階段輸入的程式文字所使用的編碼方式。 這個字元集是用於編譯器代碼中任何字串或字元常值的內部標記法。 設定此選項, 以指定當您的來源檔案包含基本執行字元集中無法顯示的字元時, 所要使用的擴充執行字元集。 您可以使用 IANA 或 ISO 字元集名稱或點 (.), 後面接著3到5位數的十進位字碼頁識別碼, 以指定要使用的字元集。 如需支援的字碼頁識別碼和字元集名稱的清單, 請參閱[字碼頁識別碼](/windows/win32/Intl/code-page-identifiers)。

根據預設, Visual Studio 會偵測位元組順序標記, 以判斷原始程式檔是否為編碼的 Unicode 格式, 例如 UTF-16 或 UTF-8。 如果找不到位元組順序標記, 則會假設原始程式檔是使用目前的使用者字碼頁進行編碼, 除非您使用 **/source-charset**選項或 **/utf-8**選項指定了字元集名稱或字碼頁。 Visual Studio 可讓您使用數C++個字元編碼方式來儲存您的原始程式碼。 如需來源和執行字元集的詳細資訊, 請參閱語言檔中的[字元集](../../cpp/character-sets.md)。

如果您想要將來源字元集和執行字元集設定為 UTF-8, 您可以使用 **/utf-8**編譯器選項做為快捷方式。 這相當於在命令列上指定 **/source-charset: utf-8/execution-charset: utf-8** 。 根據預設, 這些選項中的任何一個也會啟用 **/validate-charset**選項。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 展開 [設定**屬性**]、[ **CC++/** ]、[**命令列**] 資料夾。

1. 在 [**其他選項**] 中, 新增 **/execution-charset**選項, 並指定您慣用的編碼方式。

1. 選取 [確定] 儲存您的變更。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[/source-charset (設定來源字元集)](source-charset-set-source-character-set.md)<br/>
[/utf-8 (將來源和可執行檔字元集設定為 UTF-8)](utf-8-set-source-and-executable-character-sets-to-utf-8.md)<br/>
[/validate-charset (驗證字元是否相容)](validate-charset-validate-for-compatible-characters.md)
