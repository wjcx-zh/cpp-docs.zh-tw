---
title: HLSL 屬性頁： 輸出檔 |Microsoft 文件
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
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="hlsl-property-pages-output-files"></a>HLSL 屬性頁：輸出檔
若要設定下列屬性的 HLSL 編譯器 (fxc.exe)，使用其**輸出檔**屬性。 如需有關如何存取資訊**輸出檔**屬性頁的 HLSL 資料夾中，請參閱[使用專案屬性](../ide/working-with-project-properties.md)。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **標頭的變數名稱**  
 指定的陣列，用來編碼 HLSL 物件程式碼的名稱。 HLSL 編譯器輸出的標頭檔中包含陣列。 標頭檔的名稱由指定**標頭檔名稱**屬性。  
  
 這個屬性會對應至 **/Vn [name]** 命令列引數。  
  
 **標頭檔名稱**  
 指定的是 HLSL 編譯器輸出的標頭檔的名稱。 標頭包含編碼為陣列的 HLSL 物件程式碼。 陣列的名稱由指定**標頭的變數名稱**屬性。  
  
 這個屬性會對應至 **/Fh [name]** 命令列引數。  
  
 **目的檔名稱**  
 指定是 HLSL 編譯器輸出的物件檔案的名稱。 根據預設，此值是 **$(OutDir) %（檔名）.cso**。  
  
 這個屬性會對應至 **/Fo [名稱]** 命令列引數。  
  
 **組合語言的輸出**  
 **組件僅列出 (/ Fc)** 輸出只組合語言的陳述式。 **組譯程式碼和十六進位 (/ Fx)** 至輸出組件語言陳述式和對應作業程式碼以十六進位方式。 根據預設，清單不是輸出。  
  
 **組合語言輸出檔**  
 指定的是 HLSL 編譯器的輸出組件清單檔的名稱。  
  
 這個屬性會對應至 **/Fc [name]** 和 **/Fx [name]** 命令列引數。  
  
## <a name="see-also"></a>另請參閱  
 [HLSL 屬性頁](../ide/hlsl-property-pages.md)   
 [HLSL 屬性頁： 一般](../ide/hlsl-property-pages-general.md)   
 [HLSL 屬性頁：進階](../ide/hlsl-property-pages-advanced.md)