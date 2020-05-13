---
title: /Yl (插入偵錯程式庫的 PCH 參考)
ms.date: 01/29/2018
f1_keywords:
- /yl
helpviewer_keywords:
- -Yl compiler option [C++]
- Yl compiler option [C++]
- /Yl compiler option [C++]
ms.assetid: 8e4a396a-6790-4a9f-8387-df015a3220e7
ms.openlocfilehash: 816ba66c94e616407a8891cd149a41e44e29358d
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825713"
---
# <a name="yl-inject-pch-reference-for-debug-library"></a>/Yl (插入偵錯程式庫的 PCH 參考)

**/Yl**選項會在先行編譯標頭檔中產生唯一符號，並在使用先行編譯標頭檔的所有物件檔案中插入這個符號的參考。

## <a name="syntax"></a>語法

>**/Yl**\
>**/Yl**_名稱_\
>**Yl**

### <a name="arguments"></a>引數

*name*<br/>
選擇性名稱，用來做為唯一符號的一部分。

*\-*<br/>
虛線（-）會明確停用 **/Yl**編譯器選項。

## <a name="remarks"></a>備註

**/Yl**編譯器選項會在使用[/yc](yc-create-precompiled-header-file.md)選項建立的先行編譯標頭檔中，建立唯一的符號定義。 這個符號的參考會使用[/yu](yu-use-precompiled-header-file.md)編譯器選項，自動插入包含先行編譯標頭檔的所有檔案中。 當使用 **/yc**來建立先行編譯標頭檔時，預設會啟用 **/Yl**選項。

**/Yl**_name_選項是用來建立先行編譯標頭檔中的可辨識符號。 編譯器會使用*name*引數做為它所建立之裝飾符號名稱的一部分， `__@@_PchSym_@00@...@name`類似于，其中省略號（...）代表唯一的編譯器所產生的字元字串。 如果省略*name*引數，編譯器會自動產生符號名稱。 一般來說，您不需要知道符號的名稱。 不過，當您的專案使用多個先行編譯標頭檔時， **/Yl**_名稱_選項可能有助於判斷哪些物件檔案使用哪一個先行編譯的標頭。 您可以使用 [*名稱*] 做為搜尋字串，以在傾印檔案中尋找符號參考。

**/Yl-** 會停用預設行為，而且不會在先行編譯標頭檔中放入識別符號。 包含這個先行編譯標頭檔的已編譯檔案不會取得一般符號參考。

若未指定 **/yc** ，任何 **/Yl**選項都不會有任何作用，但如果已指定，則必須符合指定 **/yc**時所傳遞的任何 **/Yl**選項。

如果您使用 **/Yl-**、 **/yc**和[/Z7](z7-zi-zi-debug-information-format.md)選項來建立先行編譯標頭檔，則會將偵錯工具資訊儲存在用來建立先行編譯標頭檔之來源檔案的目的檔中，而不是個別的 .pdb 檔案。 如果此物件檔案接著成為程式庫的一部分，則使用此程式庫和先行編譯標頭檔的組建中可能會發生[LNK1211](../../error-messages/tool-errors/linker-tools-error-lnk1211.md)錯誤或[LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md)警告，如果用來建立先行編譯標頭檔的來源檔案未定義任何符號本身。 連結器可能會在程式庫用戶端中未參考物件檔案中的任何內容時，將物件檔案連同相關聯的調試資訊一併排除。 若要解決這個問題，當您使用 **/yc**建立先行編譯標頭檔時，請指定 **/Yl** （或移除 **/Yl-** 選項）。 這可確保包含偵錯工具資訊之程式庫中的物件檔案，會在您的組建中連結。

如需先行編譯標頭檔的詳細資訊，請參閱：

- [/Y (先行編譯標頭檔)](y-precompiled-headers.md)

- [先行編譯標頭檔](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性** > ] [**c/c + +** > **命令列**] 屬性頁。

1. 在 [**其他選項**] 方塊中新增 **/Yl**_name_編譯器選項。 選取 [確定]**** 儲存您的變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>＞。

## <a name="see-also"></a>請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
