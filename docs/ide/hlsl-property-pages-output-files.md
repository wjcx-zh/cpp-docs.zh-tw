---
title: HLSL 屬性頁：輸出檔 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.FXCompilerTool.AssemblerOutput
- VC.Project.FXCompilerTool.ObjectFileOutput
- VC.Project.FXCompilerTool.HeaderFileOutput
- VC.Project.FXCompilerTool.VariableName
- VC.Project.FXCompilerTool.AssemblerOutputFile
dev_langs:
- C++
ms.assetid: c5ba1e72-30de-43eb-a15a-5b0ae58e55c2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4fd1dc3ba92201567f24aa84ff8dddcd96798b38
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339192"
---
# <a name="hlsl-property-pages-output-files"></a>HLSL 屬性頁：輸出檔
若要設定 HLSL 編譯器 (fxc.exe) 的下列屬性，請使用其 [輸出檔案] 屬性。 如需如何存取 HLSL 資料夾中 [輸出檔案] 屬性頁的資訊，請參閱[使用專案屬性](../ide/working-with-project-properties.md)。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **標頭變數名稱**  
 指定用來編碼 HLSL 目的碼之陣列的名稱。 此陣列會包含在 HLSL 編譯器輸出的標頭檔中。 標頭檔的名稱是由 [標頭檔名] 屬性指定。  
  
 此屬性會對應至 **/Vn[name]** 命令列引數。  
  
 **標頭檔名**  
 指定 HLSL 編譯器輸出之標頭檔的名稱。 此標頭包含編碼為陣列的 HLSL 目的碼。 陣列的名稱是由 [標頭變數名稱] 屬性指定。  
  
 此屬性會對應至 **/Fh[name]** 命令列引數。  
  
 **目的檔名稱**  
 指定 HLSL 編譯器輸出之目的檔的名稱。 預設值為 **$(OutDir)%(Filename).cso**。  
  
 此屬性會對應至 **/Fo[name]** 命令列引數。  
  
 **組合語言輸出**  
 [僅列出組譯碼 (/Fc)] 只輸出組合語言陳述式。 [組譯碼和十六進位 (/Fx)] 同時輸出組合語言陳述式及十六進位格式的對應作業碼。 預設不會輸出任何清單。  
  
 **組譯工具輸出檔**  
 指定 HLSL 編譯器輸出之組件清單檔的名稱。  
  
 此屬性會對應至 **/Fc[name]** 和 **/Fx [name]** 命令列引數。  
  
## <a name="see-also"></a>請參閱  
 [HLSL 屬性頁](../ide/hlsl-property-pages.md)   
 [HLSL 屬性頁：一般](../ide/hlsl-property-pages-general.md)   
 [HLSL 屬性頁：進階](../ide/hlsl-property-pages-advanced.md)