---
title: "-/Qifist （抑制 _ftol） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /qifist
dev_langs:
- C++
helpviewer_keywords:
- QIfist compiler option [C++]
- -QIfist compiler option [C++]
- /QIfist compiler option [C++]
ms.assetid: 1afd32a5-f658-4b66-85f4-e0ce4cb955bd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7377824b45027318a21f464650ecbc837a76d31c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="qifist-suppress-ftol"></a>/QIfist (抑制 _ftol)
已取代。 在必須從浮點類型轉換為整數類型時，抑制對 Helper 函式 `_ftol` 的呼叫。  
  
## <a name="syntax"></a>語法  
  
```  
/QIfist  
```  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  **/Qifist**僅供以編譯器為目標 x86; 這個編譯器選項不適用於為目標的編譯器[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]Arm。  
  
 從浮點類型轉換成整數類資料類型，除了`_ftol`函式確保浮點數的單位 (FPU) 的捨入模式是趨近於零 （截斷），藉由設定 10 和 11 位元的控制字組。 這可確保，從浮點類型轉換成整數類資料類型發生 （捨棄的數字的小數部分） 與 ANSI C 標準所述。 當使用**/QIfist**，這項保證不再適用。 捨入模式將會是其中四個 Intel 參考手冊所述：  
  
-   四捨五入到最接近 （偶數如果等距）  
  
-   往負無限大方向捨入  
  
-   捨入朝向正無限大  
  
-   趨近零捨入  
  
 您可以使用[_control87、 _controlfp、 \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) C 執行階段函式，以修改 FPU 捨入行為。 捨入模式 FPU 的預設值是"趨向最接近。 」 使用**/QIfist**可以改善效能的應用程式，但不風險。 您應該先徹底測試您的程式碼所依賴的程式碼以在建置之前捨入模式**/QIfist**在實際執行環境。  
  
 [/arch (x86)](../../build/reference/arch-x86.md)和**/QIfist**不能在相同編譯單位。  
  
> [!NOTE]
>  **/Qifist**是未作用中預設因為捨入位元也會影響到浮點數的浮點點捨入 （發生於每次計算之後），因此當您設定的旗標 （趨近於零） 的 C 樣式捨入，您的浮點計算可能會不同。 **/Qifist**不應使用如果截斷的小數部分的浮點數的預期行為取決於您的程式碼。 如果您不確定，請勿使用**/QIfist**。  
  
 **/QIfist**選項已被取代，在 Visual Studio 2005 中啟動。 編譯器已大幅改進浮點數 int 轉換速度。 如需已被取代的編譯器選項的清單，請參閱**已取代及移除的編譯器選項**中[依分類排列的編譯器選項](../../build/reference/compiler-options-listed-by-category.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 [C/C++]  資料夾。  
  
3.  按一下 [命令列]  屬性頁。  
  
4.  在 [其他選項]  方塊中，輸入編譯器選項。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>請參閱  
 [/Q 選項 （低階運算）](../../build/reference/q-options-low-level-operations.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)