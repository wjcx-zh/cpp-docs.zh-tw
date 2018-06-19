---
title: '@ （指定編譯器回應檔） |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '@'
dev_langs:
- C++
helpviewer_keywords:
- response files, C/C++ compiler
- '@ compiler option'
- cl.exe compiler, specifying response files
ms.assetid: 400fffee-909d-4f60-bf76-45833e822685
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f291ed9a0ccc86ea1ef6fe6703205d76cdcd0fa1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369574"
---
# <a name="-specify-a-compiler-response-file"></a>@ (指定編譯器回應檔)
指定編譯器回應檔。  
  
## <a name="syntax"></a>語法  
  
```  
@response_file  
```  
  
## <a name="arguments"></a>引數  
 `response_file`  
 包含編譯器命令的文字檔。  
  
## <a name="remarks"></a>備註  
 回應檔案可以包含任何命令，您會在命令列上指定。 如果您的命令列引數超過 127 個字元，這會很有用。  
  
 不能指定**@** 選項從回應檔內。 也就是說，回應檔無法內嵌另一個回應檔案。  
  
 從命令列中，您可以指定多個回應檔選項 (例如， `@respfile.1 @respfile.2`) 您的需要。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
-   回應檔不能從開發環境中指定，而且必須在命令列指定。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   無法以程式設計方式變更這個編譯器選項。  
  
## <a name="see-also"></a>另請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)