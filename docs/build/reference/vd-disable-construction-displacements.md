---
title: "-vd （停用建構替代） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /vd
dev_langs:
- C++
helpviewer_keywords:
- -vd0 compiler option [C++]
- vd1 compiler option [C++]
- /vdn (Disable Construction Displacement) compiler option
- constructor displacements
- vtordisp fields
- /vd0 compiler option [C++]
- -vd1 compiler option [C++]
- /vd1 compiler option [C++]
- displacements compiler option
- vd0 compiler option [C++]
- Disable Construction Displacements compiler option
ms.assetid: 93258964-14d7-4b1c-9cbc-d6f4d74eab69
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b945c4a3191554d5299522ff376772d6362a616c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="vd-disable-construction-displacements"></a>/vd (停用建構替代)
## <a name="syntax"></a>語法  
  
```  
/vdn  
```  
  
## <a name="arguments"></a>引數  
 `0`  
 隱藏 vtordisp 建構函式/解構函式替代成員。 選擇此選項只有在特定的所有類別建構函式和解構函式都呼叫虛擬函式實際上。  
  
 `1`  
 可讓隱藏的 vtordisp 建構函式/解構函式替代成員的建立。 這項選擇是預設值。  
  
 `2`  
 可讓您使用[dynamic_cast 運算子](../../cpp/dynamic-cast-operator.md)所建構的物件上。 例如，從虛擬基底類別的 dynamic_cast 在衍生類別。  
  
 **/vd2**將 vtordisp 欄位時，您必須具有虛擬函式的虛擬基底。 **/vd1**應已足夠。 最常見情況**/vd2**是必要的虛擬基底中的唯一的虛擬函式時解構函式。  
  
## <a name="remarks"></a>備註  
 這些選項只適用於使用虛擬基底的 c + + 程式碼。  
  
 [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]實作 c + + 建構位移支援使用虛擬繼承的情況。 建構替代解決問題，當虛擬函式，宣告虛擬基底和衍生類別中覆寫時，建立，進一步衍生類別的建構期間從建構函式呼叫。  
  
 虛擬函式可能會收到不正確的問題是`this`指標因此虛擬的替代間的不一致的基底類別和其衍生類別的替代。 解決方案可提供單一建構替代調整，針對每個虛擬基底類別的呼叫 vtordisp 欄位。  
  
 根據預設，每當程式碼定義使用者定義的建構函式和解構函式，而且也會覆寫虛擬函式的虛擬基底時，會採用 vtordisp 欄位。  
  
 這些選項會影響整個原始程式檔。 使用[vtordisp](../../preprocessor/vtordisp.md)隱藏並再重新啟用 vtordisp 欄位類別的類別為基礎。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 [C/C++]  資料夾。  
  
3.  按一下 [命令列]  屬性頁。  
  
4.  在 [其他選項]  方塊中，輸入編譯器選項。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)