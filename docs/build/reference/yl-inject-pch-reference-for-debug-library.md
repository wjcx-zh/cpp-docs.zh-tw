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
ms.openlocfilehash: 92e47836e0fdae077defa0fe35b515ab4ca20a66
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316245"
---
# <a name="yl-inject-pch-reference-for-debug-library"></a>/Yl (插入偵錯程式庫的 PCH 參考)

**/Yl**選項在先行編譯標頭檔中，產生唯一的符號，並使用先行編譯標頭的所有目的檔中插入這個符號的參考。

## <a name="syntax"></a>語法

>**/Yl**
> **/Yl**_name_
> **/Yl-**

### <a name="arguments"></a>引數

*name*<br/>
選擇性的名稱，做為唯一的符號的一部分。

*\-*<br/>
虛線 （-） 明確停用 **/Yl**編譯器選項。

## <a name="remarks"></a>備註

**/Yl**編譯器選項使用建立先行編譯標頭檔中建立唯一的符號定義[/Yc](yc-create-precompiled-header-file.md)選項。 使用包含先行編譯標頭的所有檔案中，會自動插入這個符號的參考[/Yu](yu-use-precompiled-header-file.md)編譯器選項。 **/Yl**預設會啟用選項時 **/Yc**用來建立先行編譯標頭檔。

**/Yl**_名稱_選項用來建立先行編譯標頭檔中的識別符號。 編譯器會使用*名稱*引數做為裝飾的符號名稱的一部分建立，類似於`__@@_PchSym_@00@...@name`，其中唯一的編譯器產生的省略符號 （...） 代表字元字串。 如果*名稱*省略引數，編譯器會自動產生的符號名稱。 一般來說，您不需要知道的符號名稱。 不過，當您的專案使用一個以上的先行編譯標頭檔時，才 **/Yl**_名稱_選項可以用來以判斷哪一個物件檔案使用先行編譯標頭。 您可以使用*名稱*為搜尋字串來傾印檔案中尋找符號參考。

**/Yl-** 停用的預設行為，並不會讓先行編譯標頭檔中識別的符號。 編譯過的檔案，包含此先行編譯標頭不會收到一般的符號參考。

當 **/Yc**未指定任何 **/Yl**選項沒有任何作用，但如果指定它必須符合任何 **/Yl**選項傳遞時 **/Yc**是指定此項目。

如果您使用 **/Yl-**， **/Yc**並[/z7](z7-zi-zi-debug-information-format.md)選項來建置先行編譯標頭檔，偵錯資訊會儲存在原始程式檔，用來建立的物件檔案先行編譯標頭，而非個別的.pdb 檔案。 如果這個物件檔案然後已變更的程式庫的一部分[LNK1211](../../error-messages/tool-errors/linker-tools-error-lnk1211.md)錯誤或[LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md)警告可能會發生在組建中，使用此程式庫和先行編譯標頭檔，如果原始程式檔來建立先行編譯標頭檔並未定義任何符號本身。 連結器可能會排除目的檔的連結，以及相關聯的偵錯資訊，在目的檔中為 nothing 參考在媒體櫃用戶端時。 若要解決此問題，請指定 **/Yl** (或移除 **/Yl-** 選項) 當您使用 **/Yc**建立先行編譯標頭檔。 這可確保從包含偵錯資訊的程式庫目的檔，取得連結在組建中。

如需有關先行編譯標頭的詳細資訊，請參閱：

- [/Y (先行編譯標頭檔)](y-precompiled-headers.md)

- [先行編譯標頭檔](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 選取 **組態屬性** > **C /C++** > **命令列**屬性頁。

1. 新增 **/Yl**_名稱_中的編譯器選項**其他選項** 方塊中。 選取 [確定] 儲存您的變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
