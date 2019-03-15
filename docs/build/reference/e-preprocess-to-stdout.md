---
title: /E (前置處理至 stdout)
ms.date: 11/04/2016
f1_keywords:
- /e
helpviewer_keywords:
- -E compiler option [C++]
- /E compiler option [C++]
- preprocessor output, copy to stdout
- preprocessor output
ms.assetid: ddbb1725-d950-4978-ab2f-30a5cd7b778c
ms.openlocfilehash: 710be7e1dfc4de89bc1eed3e23e4803c561da10c
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817348"
---
# <a name="e-preprocess-to-stdout"></a>/E (前置處理至 stdout)

前置處理 C 和 c + + 原始程式檔，並將前置處理過的檔案複製到標準輸出裝置。

## <a name="syntax"></a>語法

```
/E
```

## <a name="remarks"></a>備註

在此程序，執行所有的前置處理器指示詞、 巨集展開會執行，而且會移除註解。 若要保留的前置處理過的輸出中的註解，請使用[/C （保留註解在前置處理期間）](c-preserve-comments-during-preprocessing.md)以及編譯器選項。

**/E**加入`#line`開頭和結尾的每個包含的檔案，以及條件式編譯的前置處理器指示詞所移除的行環繞輸出指示詞。 這些指示詞重新編號前置處理過的檔案的行。 如此一來，後續階段的處理期間產生的錯誤，請參閱原始程式檔，而不是前置處理過的檔案中的行的行號。

**/E**選項會抑制編譯。 您必須重新提交編譯的前置處理過的檔案。 **/E**也會隱藏輸出檔案，從 **/FA**， **/Fa**，和 **/Fm**選項。 如需詳細資訊，請參閱 < [/FA、 /Fa （清單檔）](fa-fa-listing-file.md)並[/Fm （命名對應檔）](fm-name-mapfile.md)。

若要抑制`#line`指示詞，使用[/EP （前置處理至 stdout 不 #line 指示詞）](ep-preprocess-to-stdout-without-hash-line-directives.md)選項。

若要將前置處理過的輸出傳送到的檔案，而非`stdout`，使用[/P （前置處理至檔案）](p-preprocess-to-a-file.md)選項。

若要隱藏`#line`指示詞和傳送前置處理過的輸出至檔案，使用 **/P**並 **/EP**一起。

您無法使用先行編譯標頭 **/E**選項。

請注意，在前置處理個別的檔案，不會產生空格之後權杖。 這可以產生不合法的程式，或有非預期的副作用。 下列程式會編譯成功：

```
#define m(x) x
m(int)main( )
{
   return 0;
}
```

不過，如果您使用：

```
cl -E test.cpp > test2.cpp
```

`int main` 不正確地將會在 test2.cpp `intmain`。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 [命令列]  屬性頁。

1. 輸入中的編譯器選項**其他選項** 方塊中。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>。

## <a name="example"></a>範例

下列命令列會前置處理`ADD.C`，保留註解，新增`#line`指示詞，並顯示標準輸出裝置上的結果：

```
CL /E /C ADD.C
```

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器的命令列語法](compiler-command-line-syntax.md)
