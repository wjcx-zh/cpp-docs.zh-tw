---
title: /F (設定堆疊大小)
ms.date: 11/04/2016
f1_keywords:
- /f
helpviewer_keywords:
- set stack size compiler option
- F compiler option [C++]
- -F compiler option [C++]
- /F compiler option [C++]
- stack, setting size
ms.assetid: 17320b6f-8305-445b-9ec2-75833f4b29e0
ms.openlocfilehash: 69d26a4e4634ea60457d75bc97d2266036d11e10
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525524"
---
# <a name="f-set-stack-size"></a>/F (設定堆疊大小)

設定程式的堆疊大小 （位元組）。

## <a name="syntax"></a>語法

> **/F** *數目*

## <a name="arguments"></a>引數

*數字*<br/>
堆疊大小 （位元組）。

## <a name="remarks"></a>備註

未選取這個選項的堆疊大小預設為 1 MB。 *數字*引數可以是以十進位數或 C 語言表示法。 引數的範圍可從 1 至連結器接受的最大堆疊大小。 連結器會無條件進位到最接近的 4 個位元組指定的值。 之間的間距 **/F**並*數目*是選擇性的。

您可能需要增加的堆疊大小，如果您的程式取得堆疊溢位 」 訊息。

您也可以藉由設定堆疊大小：

- 使用 **/堆疊**連結器選項。 如需詳細資訊，請參閱 < [/堆疊](../../build/reference/stack.md)。

- 使用 EDITBIN 的.exe 檔案。 如需詳細資訊，請參閱 < [EDITBIN 參考](../../build/reference/editbin-reference.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性** > **C/c + +** > **命令列**屬性頁。

1. 在 [其他選項]  方塊中，輸入編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)