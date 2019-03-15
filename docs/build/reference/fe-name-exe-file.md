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
ms.openlocfilehash: 5901ef1997cfea84c97b6d91b30335ff7dbc1d9f
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818046"
---
# <a name="fe-name-exe-file"></a>/Fe (命名 EXE 檔案)

指定的名稱和.exe 檔或 DLL 編譯器所建立的目錄。

## <a name="syntax"></a>語法

> **/Fe**[_pathname_] **/Fe:** _路徑名稱_

### <a name="arguments"></a>引數

*pathname*<br/>
相對或絕對路徑和基底檔案名稱或目錄或用於產生的可執行檔的基底檔案名稱上的相對或絕對路徑。

## <a name="remarks"></a>備註

**/Fe**選項可讓您指定的輸出目錄、 輸出可執行檔的名稱，或兩者，產生的可執行檔。 如果*pathname*路徑分隔符號結尾 (**&#92;**)，則會假設為指定輸出目錄。 否則的最後一個元件*pathname*做為輸出檔基底名稱，與其他*路徑名稱*指定的輸出目錄。 如果*pathname*並沒有任何路徑分隔符號，則會假設為目前目錄中指定輸出檔案名稱。 *Pathname*必須以雙引號括住 (**"**) 如果它包含不能在短的路徑，例如空格、 任何字元擴充字元或路徑元件超過八個字元長。

當 **/Fe**未指定選項，或在基底的檔案時未指定名稱*pathname*，該編譯器會產生輸出檔案使用指定的第一個來源或物件檔案的基底名稱的預設名稱在命令列和副檔名為.exe 或.dll 的內容。

如果您指定[/c （編譯而不連結）](c-compile-without-linking.md)選項時， **/Fe**沒有任何作用。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 開啟**組態屬性** > **連結器** > **一般**屬性頁。

1. 修改**輸出檔**屬性。 選取 [確定] 儲存您的變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>。

## <a name="example"></a>範例

下列命令列編譯並連結目前的目錄中的所有 C 原始程式檔。 產生的可執行檔為 PROCESS.exe，建立在 「 C:\Users\User Name\repos\My Project\bin"的目錄。

```
CL /Fe"C:\Users\User Name\repos\My Project\bin\PROCESS" *.C
```

## <a name="example"></a>範例

下列命令列建立可執行檔中的`C:\BIN`具有相同的基底名稱為第一個原始程式檔中目前的目錄：

```
CL /FeC:\BIN\ *.C
```

## <a name="see-also"></a>另請參閱

[輸出檔 (/F) 選項](output-file-f-options.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器的命令列語法](compiler-command-line-syntax.md)<br/>
[指定路徑名稱](specifying-the-pathname.md)<br/>
