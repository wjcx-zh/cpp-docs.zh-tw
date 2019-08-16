---
title: /validate-charset (驗證字元是否相容)
ms.date: 02/06/2019
f1_keywords:
- /validate-charset
- validate-charset
helpviewer_keywords:
- /validate-charset compiler option
ms.assetid: 50360fd0-4d32-4a4f-95d0-53d38c12ad4c
ms.openlocfilehash: 2390aa98b9416eb538f529c8c370c888cccf4734
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498165"
---
# <a name="validate-charset-validate-for-compatible-characters"></a>/validate-charset (驗證字元是否相容)

驗證來源檔案文字僅包含以 UTF-8 表示的字元。

## <a name="syntax"></a>語法

```
/validate-charset[-]
```

## <a name="remarks"></a>備註

您可以使用 **/validate-charset**選項來驗證原始程式碼是否只包含可在來源字元集和執行字元集中表示的字元。 當您指定 **/source-charset**、 **/execution-charset**或 **/utf-8**編譯器選項時, 就會自動啟用這種檢查。 您可以藉由指定 **/validate-charset-** 選項來明確停用這項檢查。

根據預設, Visual Studio 會偵測位元組順序標記, 以判斷原始程式檔是否為編碼的 Unicode 格式, 例如 UTF-16 或 UTF-8。 如果找不到位元組順序標記, 則會假設原始程式檔是使用目前的使用者字碼頁進行編碼, 除非您使用 **/utf-8**或 **/source-charset**選項來指定字碼頁。 Visual Studio 可讓您使用數C++個字元編碼方式來儲存您的原始程式碼。 如需來源和執行字元集的詳細資訊, 請參閱語言檔中的[字元集](../../cpp/character-sets.md)。 如需支援的字碼頁識別碼和字元集名稱的清單, 請參閱[字碼頁識別碼](/windows/win32/Intl/code-page-identifiers)。

Visual Studio 在來源字元集和執行字元集之間進行轉換時, 會使用 UTF-8 做為內部字元編碼。 如果來源檔案中的字元無法在執行字元集中表示, 則 UTF-8 轉換會替代問號 '？ ' 字元。 如果發生這種情況, **/validate-charset**選項會讓編譯報告警告。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 展開 [設定**屬性**]、[ **CC++/** ]、[**命令列**] 資料夾。

1. 在 [**其他選項**] 中, 新增 **/validate-charset**選項, 並指定您慣用的編碼方式。

1. 選取 [確定] 儲存您的變更。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[/execution-charset (設定執行字元集)](execution-charset-set-execution-character-set.md)<br/>
[/source-charset (設定來源字元集)](source-charset-set-source-character-set.md)<br/>
[/utf-8 (將來源和可執行檔字元集設定為 UTF-8)](utf-8-set-source-and-executable-character-sets-to-utf-8.md)
