---
title: /Fe (命名 EXE 檔案)
ms.date: 11/04/2016
f1_keywords:
- /fe
helpviewer_keywords:
- -Fe compiler option [C++]
- executable files, renaming
- rename file compiler option [C++]
- /Fe compiler option [C++]
- Fe compiler option [C++]
ms.assetid: 49f594fd-5e94-45fe-a1bf-7c9f2abb6437
ms.openlocfilehash: 72eada34c6a64a8b4591afbee03b686f3da3ee11
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685407"
---
# <a name="fe-name-exe-file"></a>/Fe (命名 EXE 檔案)

指定編譯器所建立之 .exe 檔案或 DLL 的名稱和目錄。

## <a name="syntax"></a>語法

> **/Fe**[_pathname_] \
> **/Fe：** _pathname_

### <a name="arguments"></a>引數

*路徑*<br/>
要用於產生之可執行檔的相對或絕對路徑和基底檔案名，或目錄的相對或絕對路徑，或基底檔案名。

## <a name="remarks"></a>備註

**/Fe**選項可讓您指定所產生之可執行檔的輸出目錄、輸出可執行檔名稱或兩者。 如果 *pathname* 以路徑分隔符號結束 (**&#92;**) ，則假設只指定輸出目錄。 否則，會使用 *pathname* 的最後一個元件做為輸出檔案基底名稱，而 *pathname* 的其餘部分則會指定輸出目錄。 如果 *pathname* 沒有任何路徑分隔符號，則會假設為在目前的目錄中指定輸出檔名稱。 *Pathname*必須用雙引號括住 (**"**) 如果它包含不能在短路徑中的任何字元，例如空格、擴充字元或路徑元件長度超過8個字元。

當未指定 **/Fe** 選項，或在 *pathname*中未指定檔案基底名稱時，編譯器會使用命令列上指定之第一個來源或目的檔的基底名稱，以及副檔名 .exe 或 .dll，為輸出檔案提供預設名稱。

如果您指定 [/c (編譯但不連結) ](c-compile-without-linking.md) 選項，則 **/Fe** 不會有任何作用。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 開啟 [設定**屬性**  >  **連結器**  >  **一般**] 屬性頁。

1. 修改 **輸出檔案** 屬性。 選取 [確定]**** 儲存您的變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>。

## <a name="examples"></a>範例

下列命令列會編譯並連結目前目錄中的所有 C 原始程式檔。 產生的可執行檔名稱 PROCESS.exe，並在 "C:\Users\User Name\repos\My Project\bin" 目錄中建立。

```
CL /Fe"C:\Users\User Name\repos\My Project\bin\PROCESS" *.C
```

下列命令列將以 `C:\BIN` 與目前目錄中第一個原始程式檔相同的基底名稱，在中建立可執行檔：

```
CL /FeC:\BIN\ *.C
```

## <a name="see-also"></a>另請參閱

[輸出檔案 (/F) 選項](output-file-f-options.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[指定路徑名稱](specifying-the-pathname.md)<br/>
