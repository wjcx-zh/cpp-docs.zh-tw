---
title: "-連結 （傳遞選項給連結器） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /link
dev_langs: C++
helpviewer_keywords:
- /link compiler option [C++]
- pass options to linker
- link compiler option [C++]
- linker [C++], passing options to
- -link compiler option [C++]
- cl.exe compiler [C++], passing options to linker
ms.assetid: 16902a94-c094-4328-841f-3ac94ca04848
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d6732f5a2b144172939e23af4addb37b7605de11
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="link-pass-options-to-linker"></a>/link (傳遞選項給連結器)
將一或多個連結器選項傳遞至連結器。  
  
## <a name="syntax"></a>語法  
  
```  
/link linkeroptions  
```  
  
## <a name="arguments"></a>引數  
 `linkeroptions`  
 連結器選項或傳遞至連結器的選項。  
  
## <a name="remarks"></a>備註  
 **/Link> >**選項和其連結器選項必須出現在任何檔名和 CL 選項之後。 不需要之間的空間**/link> >**和`linkeroptions`。 如需詳細資訊，請參閱[設定連結器選項](../../build/reference/setting-linker-options.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**連結器**資料夾。  
  
3.  按一下 連結器屬性頁。  
  
4.  修改一或多個屬性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   無法以程式設計方式變更這個編譯器選項。  
  
## <a name="see-also"></a>請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)