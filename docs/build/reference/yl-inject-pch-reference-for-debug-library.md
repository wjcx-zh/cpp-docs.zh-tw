---
title: "-Yl （插入偵錯程式庫的 PCH 參考） |Microsoft 文件"
ms.custom: 
ms.date: 12/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /yl
dev_langs: C++
helpviewer_keywords:
- -Yl compiler option [C++]
- Yl compiler option [C++]
- /Yl compiler option [C++]
ms.assetid: 8e4a396a-6790-4a9f-8387-df015a3220e7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6e777977f6d869d2bbc28d980f6445851e54396b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="yl-inject-pch-reference-for-debug-library"></a>/Yl (插入偵錯程式庫的 PCH 參考)

**/Yl**選項建立一般符號的先行編譯標頭檔，並將這個符號中使用先行編譯標頭的所有檔案的參考。 這樣會先行編譯標頭符號的完整型別資訊提供偵錯工具中使用先行編譯標頭的所有檔案。 這個選項預設為啟用。 使用此選項可避免因為遺失使用先行編譯標頭的連結程式庫的偵錯資訊的連結器錯誤。

## <a name="syntax"></a>語法

>**/Yl**  
>**/Yl**_名稱_  
>**/Yl-**  

### <a name="arguments"></a>引數

*name*  
選擇性的名稱，用來儲存，而且在參考物件的檔案定義，或使用先行編譯標頭的符號定義。

*\-*  
虛線 （-） 明確停用**/Yl**編譯器選項。

## <a name="remarks"></a>備註

**/Yl**選項可讓偵錯工具取得類型的完整資訊先行編譯標頭中，每個檔案，其中包含先行編譯標頭中。 此選項會建立內部的符號名稱，會將用來建立先行編譯標頭的目的檔中的符號定義[/Yc](../../build/reference/yc-create-precompiled-header-file.md)選項，並插入至包含先行編譯的所有檔案中的符號參考標頭使用[/Yu](../../build/reference/yu-use-precompiled-header-file.md)編譯器選項。 因為使用先行編譯標頭的所有原始程式檔參考具名的符號，連結器永遠會連結定義在符號與相關聯的先行編譯標頭，以偵錯資訊的物件檔案。 這個選項預設為啟用。

**/Yl**_名稱_選項用來明確建立先行編譯標頭檔的識別符號。 編譯器會使用*名稱*引數，建立類似於符號\_ \_ @@ \_PchSym\_@00@..。 @*名稱*，其中省略符號 （...） 代表連結器產生的字元字串。 如果省略引數，編譯器會自動產生的符號名稱。

**/Yl-**會停用的預設行為，並不會讓包含先行編譯標頭的目的檔中識別的符號參考。 這個選項可能需要的檔案不存在的先行編譯標頭檔編譯。

如果您使用**/Yl-**， **/Yc**和[/Z7](../../build/reference/z7-zi-zi-debug-information-format.md)選項，以建置程式庫時，編譯器會建立包含偵錯資訊中所儲存的先行編譯標頭檔目的檔，而非.pdb 檔案。 [LNK1211](../../error-messages/tool-errors/linker-tools-error-lnk1211.md)錯誤或[LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md)警告可能在使用此程式庫的組建和先行編譯標頭，如果原始程式檔用來建立先行編譯標頭不會定義任何符號。 連結器可能會排除此程式庫物件檔案的連結，以及相關聯的先行編譯標頭中的偵錯資訊，在目的檔中為 nothing 媒體櫃用戶端中參考時。 若要解決此問題，請指定**/Yl**當您使用**/Yc**建立先行編譯標頭檔和**/Yu**使用它。 這可確保包含偵錯資訊的物件檔案隨附於您的組建。

如需先行編譯標頭的詳細資訊，請參閱：

- [/Y （先行編譯標頭）](../../build/reference/y-precompiled-headers.md)

- [建立先行編譯標頭檔](../../build/reference/creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選擇**命令列**中的 屬性頁**C/c + +**資料夾。

1. 新增**/Yl**_名稱_編譯器選項在**其他選項**方塊。 選擇**確定**以儲存變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)  
[設定編譯器選項](../../build/reference/setting-compiler-options.md)  
