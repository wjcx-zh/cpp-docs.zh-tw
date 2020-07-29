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
ms.openlocfilehash: a55b2a4ce72de644fe426894ab389f62bd29b204
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232686"
---
# <a name="export-exports-a-function"></a>/EXPORT (匯出函式)

依據名稱或序數或資料，從您的程式匯出函式。

## <a name="syntax"></a>語法

> **/Export：**<em>entryname</em>[**， \@ **<em>序數</em>[**，NONAME**]] [**，DATA**]

## <a name="remarks"></a>備註

**/Export**選項會指定要從程式匯出的函式或資料項目，讓其他程式可以呼叫函數或使用資料。 匯出通常是在 DLL 中定義。

*Entryname*是呼叫程式所要使用的函式或資料項目的名稱。 *序數*指定匯出資料表的索引，範圍介於1到 65535;如果您未指定*序數*，LINK 會指派一個。 **NONAME**關鍵字只會將函數匯出為序數，而不會有*entryname*。

**Data**關鍵字會指定匯出的專案是資料項目。 用戶端程式中的資料項目必須使用**extern __declspec （dllimport）** 來宣告。

有四種方法可以匯出定義，以建議的使用順序列出：

1. 原始程式碼中的[__declspec （dllexport）](../../cpp/dllexport-dllimport.md)

1. .Def 檔案中的[匯出](exports.md)語句

1. LINK 命令中的 /EXPORT 規格

1. 原始程式碼中的[批註](../../preprocessor/comment-c-cpp.md)指示詞，格式為 `#pragma comment(linker, "/export: definition ")` 。

所有這些方法都可以在同一個程式中使用。 當 LINK 建立包含匯出的程式時，它也會建立匯入程式庫，除非組建中使用 .exp 檔案。

連結使用裝飾形式的識別碼。 編譯器會在建立 .obj 檔案時裝飾識別碼。 如果在未修飾的形式中，將*entryname*指定給連結器（出現在原始程式碼中），則連結會嘗試符合名稱。 如果找不到唯一的相符項，連結就會發出錯誤訊息。 當您需要將識別碼指定給連結器時，請使用[DUMPBIN](dumpbin-reference.md)工具來取得其[裝飾的名稱](decorated-names.md)形式。

> [!NOTE]
> 請勿指定宣告為或的已裝飾形式的 C 識別碼 **`__cdecl`** **`__stdcall`** 。

如果您需要匯出未修飾函式名稱，而且根據組建設定而有不同的匯出（例如，在32位或64位組建中），您可以針對每個設定使用不同的 DEF 檔案。 （DEF 檔案中不允許預處理器條件指示詞）。或者，您可以在 `#pragma comment` 函式宣告之前使用指示詞，如下所示，其中 `PlainFuncName` 是未修飾的名稱，而是函式的 `_PlainFuncName@4` 裝飾名稱：

```cpp
#pragma comment(linker, "/export:PlainFuncName=_PlainFuncName@4")
BOOL CALLBACK PlainFuncName( Things * lpParams)
```

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定] [**屬性**] [  >  **連結器**  >  **命令列**] 屬性頁。

1. 在 [**其他選項**] 方塊中輸入選項。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱＜ <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A> ＞。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
