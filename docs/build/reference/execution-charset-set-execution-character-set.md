---
title: /execution-charset （設定執行字元集）
ms.date: 11/04/2016
f1_keywords:
- execution-charset
- /execution-charset
helpviewer_keywords:
- /execution-charset compiler option
- -execution-charset compiler option
ms.assetid: 0e02f487-2236-45bc-95f3-5760933a8f96
ms.openlocfilehash: 3535b60d7aad50f7efc5d1f32726560431ac86a3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663966"
---
# <a name="execution-charset-set-execution-character-set"></a>/execution-charset （設定執行字元集）

可讓您指定可執行檔的執行字元集。

## <a name="syntax"></a>語法

```
/execution-charset:[IANA_name|.CPID]
```

## <a name="arguments"></a>引數

*IANA_name*<br/>
IANA 定義字元集名稱。

*CPID*<br/>
字碼頁識別項。

## <a name="remarks"></a>備註

您可以使用 **/execution-charset**選項來指定執行字元集。 執行字元集是程式的您輸入到畢竟前置處理步驟在編譯階段文字所使用的編碼方式。 這個字元集用於編譯的程式碼中任何字串或字元常值的內部表示法。 設定此選項來指定原始程式檔包含基本執行字元集中可顯示的字元時所要使用的擴充的執行字元集。 您可以使用任一 IANA 或 ISO 字元集的名稱，或句點 （.） 後面接著指定要使用的字元集 3 到 5 位數十進位的字碼頁識別項。 一份支援的字碼頁識別項與設定名稱的字元，請參閱[字碼頁識別項](/windows/desktop/Intl/code-page-identifiers)。

根據預設，Visual Studio 會偵測以判斷原始程式檔是否編碼的 Unicode 格式，例如 utf-16 或 utf-8 位元組順序標記。 如果找到沒有位元組順序標記，它就會假設來源檔案編碼使用目前使用者的字碼頁，除非您已指定為字元使用設定名稱或字碼頁 **/source-charset**選項或 **/utf-8**選項。 Visual Studio 可讓您使用數種字元編碼的任何儲存您的 c + + 程式碼。 來源和執行字元集的相關資訊，請參閱[字元集](../../cpp/character-sets.md)語言文件中。

如果您想要設定來源字元集和執行字元集為 utf-8，您可以使用 **/utf-8**當作捷徑使用的編譯器選項。 它相當於指定**來源-charset:utf-8 /execution-charset:utf-8**命令列上。 任何這些選項也可讓 **/validate-charset**預設選項。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 依序展開**組態屬性**， **C/c + +**，**命令列**資料夾。

1. 在 **進階選項**，新增 **/execution-charset**選項，並指定您慣用的編碼方式。

1. 選擇**確定**以儲存變更。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)<br/>
[/source-charset (設定來源字元集)](../../build/reference/source-charset-set-source-character-set.md)<br/>
[/utf-8 (將來源和可執行檔字元集設定為 UTF-8)](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)<br/>
[/validate-charset (驗證字元是否相容)](../../build/reference/validate-charset-validate-for-compatible-characters.md)