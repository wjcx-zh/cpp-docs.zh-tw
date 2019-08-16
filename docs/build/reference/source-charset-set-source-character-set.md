---
title: /source-charset (設定來源字元集)
ms.date: 02/06/2019
f1_keywords:
- source-charset
- /source-charset
helpviewer_keywords:
- /execution-charset compiler option
ms.assetid: d3c5bf7f-526d-4ee4-acc5-c1a02a4fc481
ms.openlocfilehash: cd3e4eb3fd305ba6bdd298d18b1edb80f2b98343
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498249"
---
# <a name="source-charset-set-source-character-set"></a>/source-charset (設定來源字元集)

可讓您指定可執行檔的來源字元集。

## <a name="syntax"></a>語法

```
/source-charset:[IANA_name|.CPID]
```

## <a name="arguments"></a>引數

**IANA_name**<br/>
IANA 定義的字元集名稱。

**CPID**<br/>
字碼頁識別碼, 表示為十進位數。

## <a name="remarks"></a>備註

您可以使用 **/source-charset**選項, 指定當您的來源檔案包含未在基本來源字元集中呈現的字元時, 所要使用的擴充來源字元集。 來源字元集是用來將程式的來源文字解讀成內部標記法的編碼方式, 以在編譯之前做為前置處理階段的輸入使用。 內部標記法接著會轉換成執行字元集, 以將字串和字元值儲存在可執行檔中。 您可以使用 IANA 或 ISO 字元集名稱或點 (.), 後面接著3到5位數的十進位字碼頁識別碼, 以指定要使用的字元集。 如需支援的字碼頁識別碼和字元集名稱的清單, 請參閱[字碼頁識別碼](/windows/win32/Intl/code-page-identifiers)。

根據預設, Visual Studio 會偵測位元組順序標記, 以判斷原始程式檔是否為編碼的 Unicode 格式, 例如 UTF-16 或 UTF-8。 如果找不到位元組順序標記, 則會假設原始程式檔是使用目前的使用者字碼頁進行編碼, 除非您使用 **/source-charset**選項來指定字元集名稱或字碼頁。 Visual Studio 可讓您使用數C++個字元編碼方式來儲存您的原始程式碼。 如需有關來源和執行字元集的詳細資訊, 請參閱語言檔中的[字元集](../../cpp/character-sets.md)。

您提供的來源字元集必須將7位 ASCII 字元對應到字元集中的相同程式碼點, 否則可能會遵循許多編譯錯誤。 您的來源字元集也必須可映射到 UTF-8 所 encodable 的擴充 Unicode 字元集。 不是以 UTF-8 encodable 的字元是以實作為特定的替代方式來表示。 Microsoft 編譯器會對這些字元使用問號。

如果您想要將來源字元集和執行字元集設定為 UTF-8, 您可以使用 **/utf-8**編譯器選項做為快捷方式。 這相當於在命令列上指定 **/source-charset: utf-8/execution-charset: utf-8** 。 根據預設, 這些選項中的任何一個也會啟用 **/validate-charset**選項。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 展開 [設定**屬性**]、[ **CC++/** ]、[**命令列**] 資料夾。

1. 在 [**其他選項**] 中, 新增 **/source-charset**選項, 並指定您慣用的編碼方式。

1. 選取 [確定] 儲存您的變更。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[/execution-charset (設定執行字元集)](execution-charset-set-execution-character-set.md)<br/>
[/utf-8 (將來源和可執行檔字元集設定為 UTF-8)](utf-8-set-source-and-executable-character-sets-to-utf-8.md)<br/>
[/validate-charset (驗證字元是否相容)](validate-charset-validate-for-compatible-characters.md)
