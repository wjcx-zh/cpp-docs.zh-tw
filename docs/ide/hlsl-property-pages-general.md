---
title: "HLSL 屬性頁： 一般 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.FXCompilerTool.ShaderModel
- VC.Project.FXCompilerTool.PreprocessorDefinitions
- VC.Project.FXCompilerTool.ShaderType
- VC.Project.FXCompilerTool.EnableDebuggingInformation
- VC.Project.FXCompilerTool.AdditionalIncludeDirectories
- VC.Project.FXCompilerTool.DisableOptimizations
- VC.Project.FXCompilerTool.EntryPointName
dev_langs: C++
ms.assetid: 0e02f2a6-f123-43da-b04b-a0719a7c2b03
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: be548966f6e75afde2c137c8beab38903844667c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="hlsl-property-pages-general"></a>HLSL 屬性頁：一般
若要設定下列屬性的 HLSL 編譯器 (fxc.exe)，使用其**一般**屬性頁。 如需有關如何存取資訊**一般**屬性頁的 HLSL 資料夾中，請參閱[使用專案屬性](../ide/working-with-project-properties.md)。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **其他 Include 目錄**  
 將一個或多個目錄加入至 include 路徑。 請使用分號隔開這些目錄。  
  
 這個屬性會對應至**/I [路徑]**命令列引數。  
  
 **進入點名稱**  
 指定著色器的進入點。 根據預設，此值是**主要**。  
  
 這個屬性會對應至**/E [名稱]**命令列引數。  
  
 **停用最佳化**  
 **是 （/ Od）**停用最佳化; 否則**否**。 根據預設，此值是**是 （/ Od）**如**偵錯**組態和**否**的**發行**組態。  
  
 **/Od** HLSL 編譯器命令列引數會隱含地套用**/gfp 不一樣**命令列引數，但輸出可能不等於傳遞兩者所產生之輸出**/Od**和**/gfp 不一樣**命令列引數明確。  
  
 **啟用偵錯資訊**  
 **是 (/Zi)**以啟用偵錯資訊; 否則**否**。 根據預設，此值是**是 (/Zi)**如**偵錯**組態和**否**的**發行**組態。  
  
 **著色器類型**  
 指定著色器的類型。 不同種類的著色器實作圖形管線的不同部分。 特定種類的著色器中只會有較新的著色器模型 (這由**著色器模型**屬性) — 例如，計算著色器模型 5 中導入著色器。  
  
 這個屬性會對應至**[type]**部分**/T [type] _ [模型]** HLSL 編譯器命令列引數。 **著色器模型**屬性會指定**[模型]**引數的部分。  
  
 **著色器模型**  
 指定著色器模型。 不同的著色器模型具有不同的功能。 一般情況下，較新的著色器模型提供擴充的功能，但需要執行的著色器程式碼更現代圖形硬體。 特定種類的著色器 (所指定的**著色器類型**屬性) 只適用於較新的著色器模型 — 例如，計算著色器模型 5 中導入著色器。  
  
 這個屬性會對應至**[模型]**部分**/T [type] _ [模型]** HLSL 編譯器命令列引數。 **著色器類型**屬性會指定**[type]**引數的部分。  
  
 **前置處理器定義**  
 加入要套用至 HLSL 原始程式碼檔的一或多個前置處理器符號定義。 您可以使用分號來分隔的符號定義。  
  
 這個屬性會對應至**/D [定義]** HLSL 編譯器命令列引數。  
  
## <a name="see-also"></a>請參閱  
 [HLSL 屬性頁](../ide/hlsl-property-pages.md)   
 [HLSL 屬性頁： 進階](../ide/hlsl-property-pages-advanced.md)   
 [HLSL 屬性頁：輸出檔](../ide/hlsl-property-pages-output-files.md)