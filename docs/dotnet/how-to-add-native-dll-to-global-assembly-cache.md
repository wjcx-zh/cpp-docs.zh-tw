---
title: 如何： 將原生 DLL 加入全域組件快取 |Microsoft 文件
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], native
- GAC (global assembly cache), loading native DLLs
- native DLLs [C++]
ms.assetid: 25e8d78a-b197-4269-b4e9-237a544ab3c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b7363de172eabc664bcde1e3bf42f8cc499e4251
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33129534"
---
# <a name="how-to-add-native-dll-to-global-assembly-cache"></a>如何：將原生 DLL 加入至全域組件快取
您可以將原生 DLL (非 COM) 放入全域組件快取。  
  
## <a name="example"></a>範例  
 **/ASSEMBLYLINKRESOURCE**可讓您嵌入組件的原生 DLL。  
  
 如需詳細資訊，請參閱 [/ASSEMBLYLINKRESOURCE (連結到 .NET Framework 資源)](../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)。  
  
```  
/ASSEMBLYLINKRESOURCE:MyComponent.dll  
```  
  
## <a name="see-also"></a>另請參閱  
 [使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)