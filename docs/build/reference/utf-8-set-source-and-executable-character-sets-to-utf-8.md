---
title: /utf-8 （將來源和可執行檔字元集設定為 utf-8）
ms.date: 11/04/2016
f1_keywords:
- /utf-8
helpviewer_keywords:
- /utf-8 compiler option
ms.assetid: f0e1f3cb-6cae-46eb-9483-04ed13d9b504
ms.openlocfilehash: 5ac15c63041e76b8bb0d292868bb982c21866078
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317285"
---
# <a name="utf-8-set-source-and-executable-character-sets-to-utf-8"></a>/utf-8 （將來源和可執行檔字元集設定為 utf-8）

指定的來源字元集和執行字元集為 utf-8。

## <a name="syntax"></a>語法

```
/utf-8
```

## <a name="remarks"></a>備註

您可以使用 **/utf-8**選項來指定來源 」 和 「 執行字元集設定為使用 utf-8 編碼。 它相當於指定**來源-charset:utf-8 /execution-charset:utf-8**命令列上。 任何這些選項也可讓 **/validate-charset**預設選項。 一份支援的字碼頁識別項與設定名稱的字元，請參閱[字碼頁識別項](/windows/desktop/Intl/code-page-identifiers)。

根據預設，Visual Studio 會偵測以判斷原始程式檔是否編碼的 Unicode 格式，例如 utf-16 或 utf-8 位元組順序標記。 如果找到沒有位元組順序標記，它就會假設來源檔案編碼使用目前使用者的字碼頁，除非您已使用指定的字碼頁 **/utf-8**或 **/source-charset**選項。 Visual Studio 可讓您儲存您C++使用數種字元編碼的任何來源的程式碼。 來源和執行字元集的相關資訊，請參閱[字元集](../../cpp/character-sets.md)語言文件中。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 依序展開**組態屬性**， **C /C++**，**命令列**資料夾。

1. 在 **其他選項**，新增 **/utf-8**選項來指定您慣用的編碼方式。

1. 選取 [確定] 儲存您的變更。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[/execution-charset （設定執行字元集）](execution-charset-set-execution-character-set.md)<br/>
[/source-charset (設定來源字元集)](source-charset-set-source-character-set.md)<br/>
[/validate-charset (驗證字元是否相容)](validate-charset-validate-for-compatible-characters.md)
