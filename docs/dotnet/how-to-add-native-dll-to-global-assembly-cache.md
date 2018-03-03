---
title: "如何： 將原生 DLL 加入全域組件快取 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], native
- GAC (global assembly cache), loading native DLLs
- native DLLs [C++]
ms.assetid: 25e8d78a-b197-4269-b4e9-237a544ab3c8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: be55fd47cd6024d0660ed0c3e4594c9430f80cc2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-add-native-dll-to-global-assembly-cache"></a>如何：將原生 DLL 加入至全域組件快取
您可以將原生 DLL (非 COM) 放入全域組件快取。  
  
## <a name="example"></a>範例  
 **/ASSEMBLYLINKRESOURCE**可讓您嵌入組件的原生 DLL。  
  
 如需詳細資訊，請參閱 [/ASSEMBLYLINKRESOURCE (連結到 .NET Framework 資源)](../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)。  
  
```  
/ASSEMBLYLINKRESOURCE:MyComponent.dll  
```  
  
## <a name="see-also"></a>請參閱  
 [使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)