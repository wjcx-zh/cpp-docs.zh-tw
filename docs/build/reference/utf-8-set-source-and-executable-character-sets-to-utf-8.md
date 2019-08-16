---
title: /utf-8 (將來源和可執行檔字元集設定為 UTF-8)
ms.date: 11/04/2016
f1_keywords:
- /utf-8
helpviewer_keywords:
- /utf-8 compiler option
ms.assetid: f0e1f3cb-6cae-46eb-9483-04ed13d9b504
ms.openlocfilehash: 1ff0f23ad0758642c73b1b35d6d4dd1be20899cb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498171"
---
# <a name="utf-8-set-source-and-executable-character-sets-to-utf-8"></a>/utf-8 (將來源和可執行檔字元集設定為 UTF-8)

將來源字元集和執行字元集同時指定為 UTF-8。

## <a name="syntax"></a>語法

```
/utf-8
```

## <a name="remarks"></a>備註

您可以使用 **/utf-8**選項, 指定使用 utf-8 編碼的來源和執行字元集。 這相當於在命令列上指定 **/source-charset: utf-8/execution-charset: utf-8** 。 根據預設, 這些選項中的任何一個也會啟用 **/validate-charset**選項。 如需支援的字碼頁識別碼和字元集名稱的清單, 請參閱[字碼頁識別碼](/windows/win32/Intl/code-page-identifiers)。

根據預設, Visual Studio 會偵測位元組順序標記, 以判斷原始程式檔是否為編碼的 Unicode 格式, 例如 UTF-16 或 UTF-8。 如果找不到位元組順序標記, 則會假設原始程式檔是使用目前的使用者字碼頁進行編碼, 除非您使用 **/utf-8**或 **/source-charset**選項來指定字碼頁。 Visual Studio 可讓您使用數C++個字元編碼方式來儲存您的原始程式碼。 如需來源和執行字元集的詳細資訊, 請參閱語言檔中的[字元集](../../cpp/character-sets.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 展開 [設定**屬性**]、[ **CC++/** ]、[**命令列**] 資料夾。

1. 在 [**其他選項**] 中, 新增 **/utf-8**選項來指定您慣用的編碼方式。

1. 選取 [確定] 儲存您的變更。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[/execution-charset (設定執行字元集)](execution-charset-set-execution-character-set.md)<br/>
[/source-charset (設定來源字元集)](source-charset-set-source-character-set.md)<br/>
[/validate-charset (驗證字元是否相容)](validate-charset-validate-for-compatible-characters.md)
