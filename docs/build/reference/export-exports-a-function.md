---
title: /EXPORT (匯出函式)
ms.date: 09/05/2018
f1_keywords:
- VC.Project.VCLinkerTool.ExportFunctions
- /export
helpviewer_keywords:
- /EXPORT linker option
- EXPORT linker option
- -EXPORT linker option
ms.assetid: 0920fb44-a472-4091-a8e6-73051f494ca0
ms.openlocfilehash: a26df26849302ae1cce449f92cdeb5ee6dfd9baa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456122"
---
# <a name="export-exports-a-function"></a>/EXPORT (匯出函式)

匯出的函式依名稱或序數或資料，從您的程式。

## <a name="syntax"></a>語法

> **/EXPORT:**<em>entryname</em>[**，\@**<em>序數</em>[**，NONAME**]] [**，資料**]

## <a name="remarks"></a>備註

**/匯出**選項會指定函式或資料的項目，若要匯出從您的程式，讓其他程式可以呼叫此函式，或使用的資料。 匯出通常是在 DLL 中定義。

*Entryname*是函式或資料的項目名稱，因為它是可供呼叫端程式。 *序數*指定範圍 1 到 65535 之間的匯出資料表的索引，如果您未指定*序數*，連結會將指派其中一個。 **NONAME**關鍵字匯出函式只能做為序數，而不*entryname*。

**資料**關鍵字會指定匯出的項目是資料的項目。 必須使用宣告的用戶端程式中的資料項目**extern __declspec （dllimport)**。

有四種方法匯出定義，在 建議使用的順序列出：

1. [__declspec （dllexport)](../../cpp/dllexport-dllimport.md)原始程式碼中

1. [匯出](../../build/reference/exports.md).def 檔案中的陳述式

1. LINK 命令中的 /EXPORT 規格

1. A[註解](../../preprocessor/comment-c-cpp.md)指示詞中的原始程式碼，表單的`#pragma comment(linker, "/export: definition ")`。

所有這些方法可以用於相同的程式。 當組建的程式包含匯出的連結時，它也會建立匯入程式庫，除非在組建中使用.exp 檔。

連結使用裝飾形式的識別項。 建立的.obj 檔案時，編譯器就會裝飾識別項。 如果*entryname*指定連結器在其未裝飾形成 （因為它會出現在原始程式碼中），連結會嘗試比對的名稱。 如果它找不到所需的唯一相符項目，連結就會發出錯誤訊息。 使用[DUMPBIN](../../build/reference/dumpbin-reference.md)工具，以取得[裝飾名稱](../../build/reference/decorated-names.md)時您必須指定至連結器識別項格式。

> [!NOTE]
> 未指定 C 識別項宣告的裝飾的形式`__cdecl`或`__stdcall`。

如果您要匯出未裝飾的函式名稱，並有不同的匯出，根據組建組態 （例如，在 32 位元或 64 位元的組建），您可以使用不同的.DEF 檔，每個組態。 （條件式的前置處理器指示詞不允許在.DEF 檔中）。或者，您可以使用`#pragma comment`指示詞之前的函式宣告如下所示，其中`PlainFuncName`是未裝飾的名稱，和`_PlainFuncName@4`是函式的裝飾的名稱：

```cpp
#pragma comment(linker, "/export:PlainFuncName=_PlainFuncName@4")
BOOL CALLBACK PlainFuncName( Things * lpParams)
```

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性** > **連結器** > **命令列**屬性頁。

1. 輸入到選項**其他選項** 方塊中。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)
