---
title: HLSL 屬性頁：輸出檔
ms.date: 11/04/2016
f1_keywords:
- VC.Project.FXCompilerTool.AssemblerOutput
- VC.Project.FXCompilerTool.ObjectFileOutput
- VC.Project.FXCompilerTool.HeaderFileOutput
- VC.Project.FXCompilerTool.VariableName
- VC.Project.FXCompilerTool.AssemblerOutputFile
ms.assetid: c5ba1e72-30de-43eb-a15a-5b0ae58e55c2
ms.openlocfilehash: 6ee8042fccf2e0b635535a77d9c9a6bc68bd9999
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291544"
---
# <a name="hlsl-property-pages-output-files"></a>HLSL 屬性頁：輸出檔

若要設定 HLSL 編譯器 (fxc.exe) 的下列屬性，請使用其 [輸出檔案] 屬性。 如需有關如何存取資訊**輸出檔案**HLSL 資料夾中的屬性頁面上看到[設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。

## <a name="uielement-list"></a>UIElement 清單

- **標頭變數名稱**

   指定用來編碼 HLSL 目的碼之陣列的名稱。 此陣列會包含在 HLSL 編譯器輸出的標頭檔中。 標頭檔的名稱是由 [標頭檔名] 屬性指定。

此屬性會對應至 **/Vn[name]** 命令列引數。

- **標頭檔名**

   指定 HLSL 編譯器輸出之標頭檔的名稱。 此標頭包含編碼為陣列的 HLSL 目的碼。 陣列的名稱是由 [標頭變數名稱] 屬性指定。

此屬性會對應至 **/Fh[name]** 命令列引數。

- **目的檔名稱**

   指定 HLSL 編譯器輸出之目的檔的名稱。 預設值為 **$(OutDir)%(Filename).cso**。

此屬性會對應至 **/Fo[name]** 命令列引數。

- **組合語言輸出**

   [僅列出組譯碼 (/Fc)] 只輸出組合語言陳述式。 [組譯碼和十六進位 (/Fx)] 同時輸出組合語言陳述式及十六進位格式的對應作業碼。 預設不會輸出任何清單。

- **組譯工具輸出檔**

   指定 HLSL 編譯器輸出之組件清單檔的名稱。

   此屬性會對應至 **/Fc[name]** 和 **/Fx [name]** 命令列引數。

## <a name="see-also"></a>另請參閱

[HLSL 屬性頁](hlsl-property-pages.md)<br>
[HLSL 屬性頁：一般](hlsl-property-pages-general.md)<br>
[HLSL 屬性頁：進階](hlsl-property-pages-advanced.md)
