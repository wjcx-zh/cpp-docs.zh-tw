---
title: -Yl （插入偵錯程式庫的 PCH 參考） |Microsoft 文件
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /yl
dev_langs:
- C++
helpviewer_keywords:
- -Yl compiler option [C++]
- Yl compiler option [C++]
- /Yl compiler option [C++]
ms.assetid: 8e4a396a-6790-4a9f-8387-df015a3220e7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a73e79cd50343292ae63dfa831a7638d6444fc64
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="yl-inject-pch-reference-for-debug-library"></a>/Yl (插入偵錯程式庫的 PCH 參考)

**/Yl**選項，先行編譯標頭檔中產生唯一的符號，且此符號的參考會插入在使用先行編譯標頭的所有目的檔中。

## <a name="syntax"></a>語法

>**/Yl**  
>**/Yl**_名稱_  
>**/Yl-**  

### <a name="arguments"></a>引數

*name*  
選擇性的名稱，做為唯一的符號的一部分。

*\-*  
虛線 （-） 明確停用 **/Yl**編譯器選項。

## <a name="remarks"></a>備註

**/Yl**編譯器選項會利用建立先行編譯標頭檔中建立唯一的符號定義[/Yc](../../build/reference/yc-create-precompiled-header-file.md)選項。 這個符號的參考會自動插入包含先行編譯標頭使用的所有檔案內[/Yu](../../build/reference/yu-use-precompiled-header-file.md)編譯器選項。 **/Yl**預設會啟用選項時 **/Yc**用來建立先行編譯標頭檔。

**/Yl**_名稱_選項用來建立先行編譯標頭檔中識別的符號。 編譯器會使用*名稱*引數做為符號的裝飾的名稱的一部分建立，類似於\_ \_ @@ \_PchSym\_@00@...@*名稱*，唯一的編譯器產生的省略符號 （...） 代表字元字串的位置。 如果*名稱*省略引數，編譯器會自動產生的符號名稱。 一般來說，您不需要知道的符號名稱。 不過，當您的專案會使用一個以上的先行編譯標頭檔 **/Yl**_名稱_選項可能有助於判斷哪些物件檔案使用的先行編譯標頭。 您可以使用*名稱*為傾印檔案中尋找符號參考搜尋字串。

**/Yl-** 會停用的預設行為，並不會讓先行編譯標頭檔中識別的符號。 編譯包含此先行編譯標頭的檔案不會收到一般的符號參考。

當 **/Yc**未指定任何 **/Yl**選項沒有任何作用，但如果指定它必須符合任何 **/Yl**選項傳遞時 **/Yc**是指定。

如果您使用 **/Yl-**， **/Yc**和[/Z7](../../build/reference/z7-zi-zi-debug-information-format.md)選項來建置先行編譯標頭檔，偵錯資訊會儲存在原始程式檔，用來建立目的檔先行編譯標頭，而非個別的.pdb 檔案。 如果這個物件檔案然後對程式庫中，部分[LNK1211](../../error-messages/tool-errors/linker-tools-error-lnk1211.md)錯誤或[LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md)警告可能會發生在組建中使用此程式庫和先行編譯標頭檔，如果用來建立的原始程式檔先行編譯標頭檔並未定義任何符號本身。 連結器可能會排除目的檔的連結，以及相關聯的偵錯資訊，在目的檔中為 nothing 媒體櫃用戶端中參考時。 若要解決此問題，請指定 **/Yl** (或移除 **/Yl-** 選項) 當您使用 **/Yc**建立先行編譯標頭檔。 這可確保目的檔中包含偵錯資訊的程式庫取得連結在您的組建。

如需先行編譯標頭的詳細資訊，請參閱：

- [/Y (先行編譯標頭檔)](../../build/reference/y-precompiled-headers.md)

- [建立先行編譯標頭檔](../../build/reference/creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取**組態屬性** > **C/c + +** > **命令列**屬性頁。

1. 新增 **/Yl**_名稱_編譯器選項在**其他選項**方塊。 選擇**確定**以儲存變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)  
[設定編譯器選項](../../build/reference/setting-compiler-options.md)  
