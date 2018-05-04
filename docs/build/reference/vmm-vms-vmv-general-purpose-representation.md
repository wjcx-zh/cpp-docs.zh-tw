---
title: -vmm 的 vm，-vmv （一般用途表示） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /vms
- /vmm
- /vmv
dev_langs:
- C++
helpviewer_keywords:
- Virtual Inheritance compiler option
- general purpose representation compiler options
- vms compiler option [C++]
- vmm compiler option [C++]
- /vmm compiler option [C++]
- -vmm compiler option [C++]
- -vms compiler option [C++]
- /vms compiler option [C++]
- vmv compiler option [C++]
- /vmv compiler option [C++]
- Single Inheritance compiler option
- -vmv compiler option [C++]
ms.assetid: 0fcd7ae0-3031-4c62-a2a8-e154c8685dae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd2f79238c890d43678332203acbe9d935a54102
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="vmm-vms-vmv-general-purpose-representation"></a>/vmm、/vms、/vmv (一般用途表示)
使用時機[/vmb、 /vmg （表示方法）](../../build/reference/vmb-vmg-representation-method.md)當做[表示方法](../../build/reference/vmb-vmg-representation-method.md)。 這些選項表示尚未發生類別定義的繼承模型。  
  
## <a name="syntax"></a>語法  
  
```  
/vmm  
/vms  
/vmv  
```  
  
## <a name="remarks"></a>備註  
 請參閱下表描述的選項。  
  
|選項|描述|  
|------------|-----------------|  
|**/vmm**|指定要使用多個繼承的類別成員指標的最常見的表示。<br /><br /> 對應[繼承關鍵字](../../cpp/inheritance-keywords.md)和引數[#pragma pointers_to_members](../../preprocessor/pointers-to-members.md)是**multiple_inheritance**。<br /><br /> 此表示法大於所需的單一繼承。<br /><br /> 如果虛擬繼承模型，為其成員指標宣告的類別定義，編譯器會產生錯誤。|  
|**/vms**|指定的指標類別的成員，才能不使用任何繼承 」 或 「 單一繼承最常見的表示。<br /><br /> 對應[繼承關鍵字](../../cpp/inheritance-keywords.md)和引數[#pragma pointers_to_members](../../preprocessor/pointers-to-members.md)是**single_inheritance**。<br /><br /> 這是類別的最小成員指標表示。<br /><br /> 如果宣告成員指標類別定義的繼承模型為多重或虛擬，編譯器會產生錯誤。|  
|**/vmv**|指定要使用虛擬繼承的類別成員指標的最常見的表示。 它永遠不會造成錯誤，而且是預設值。<br /><br /> 對應[繼承關鍵字](../../cpp/inheritance-keywords.md)和引數[#pragma pointers_to_members](../../preprocessor/pointers-to-members.md)是**virtual_inheritance**。<br /><br /> 此選項需要較大的指標和額外的程式碼來解譯指標比其他選項。|  
  
 當您指定其中一個繼承模型選項時，該模型用於所有指標的類別成員，不論它們繼承的類型或指標是否宣告之前或之後的類別。 因此，如果您總是使用單一繼承類別，您可以縮小程式碼與編譯 **/vms**; 不過，如果您想要使用 （但會犧牲的最大的資料表示法） 最常見的案例，使用編譯 **/vmv**。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 [C/C++]  資料夾。  
  
3.  按一下 [命令列]  屬性頁。  
  
4.  在 [其他選項]  方塊中，輸入編譯器選項。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [/vmb、 /vmg （表示方法）](../../build/reference/vmb-vmg-representation-method.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)