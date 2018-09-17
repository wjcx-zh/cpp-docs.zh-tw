---
title: -來源-字元集 （設定來源字元集） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- source-charset
- /source-charset
dev_langs:
- C++
helpviewer_keywords:
- /execution-charset compiler option
ms.assetid: d3c5bf7f-526d-4ee4-acc5-c1a02a4fc481
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c36f898c005a989a7be78e436b560fe9a0536b57
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715061"
---
# <a name="source-charset-set-source-character-set"></a>/source-charset （設定來源字元集）

可讓您指定可執行檔的來源字元集。

## <a name="syntax"></a>語法

```
/source-charset:[IANA_name|.CPID]
```

## <a name="arguments"></a>引數

**IANA_name**<br/>
IANA 定義字元集名稱。

**CPID**<br/>
以十進位數字字碼頁識別項。

## <a name="remarks"></a>備註

您可以使用 **/source-charset**選項來指定擴充的來源字元設為原始程式檔包含基本來源字元集中的未表示的字元時使用。 來源字元集是程式的用來解譯成做為輸入之前編譯的前置處理階段的內部表示法的來源文字編碼方式。 內部表示法會轉換為執行字元集，將字串和字元值儲存在可執行檔。 您可以使用任一 IANA 或 ISO 字元集的名稱，或句點 （.） 後面接著指定要使用的字元集 3 到 5 位數十進位的字碼頁識別項。 一份支援的字碼頁識別項與設定名稱的字元，請參閱[字碼頁識別項](/windows/desktop/Intl/code-page-identifiers)。

根據預設，Visual Studio 會偵測以判斷原始程式檔是否編碼的 Unicode 格式，例如 utf-16 或 utf-8 位元組順序標記。 如果找到沒有位元組順序標記，它就會假設來源檔案編碼使用目前使用者的字碼頁，除非您指定的字元使用設定名稱或字碼頁 **/source-charset**選項。 Visual Studio 可讓您使用數種字元編碼的任何儲存您的 c + + 程式碼。 如需有關來源和執行字元集的詳細資訊，請參閱[字元集](../../cpp/character-sets.md)語言文件中。

您提供的來源字元集必須將 7 位元 ASCII 字元對應到相同的字碼指標，在您的字元集，或可能採用許多的編譯錯誤。 您的來源字元集也必須是可延伸設定 encodable utf-8 的 Unicode 字元對應。 Encodable utf-8 的字元是由實作特定替代表示。 Microsoft 編譯器會使用問號，這些字元。

如果您想要設定來源字元集和執行字元集為 utf-8，您可以使用 **/utf-8**當作捷徑使用的編譯器選項。 它相當於指定**來源-charset:utf-8 /execution-charset:utf-8**命令列上。 任何這些選項也可讓 **/validate-charset**預設選項。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 依序展開**組態屬性**， **C/c + +**，**命令列**資料夾。

1. 在 **進階選項**，新增 **/source-charset**選項，並指定您慣用的編碼方式。

1. 選擇**確定**以儲存變更。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)<br/>
[（設定執行字元集） 的 /execution-charset](../../build/reference/execution-charset-set-execution-character-set.md)
[/utf-8 （將來源和可執行檔字元集為 utf-8）](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)
[/validate-charset （驗證相容字元為單位）](../../build/reference/validate-charset-validate-for-compatible-characters.md)