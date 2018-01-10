---
title: "STL/CLR 容器項目的需求 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- C++ Standard Library, template class containers
- STL/CLR, containers
- containers, STL/CLR
- containers, C++ Standard Library
ms.assetid: 59ab240c-15bf-4701-a9f9-e7c56e5ab53f
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3317e3c9349963fc24b37b421def05c475732fd8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="requirements-for-stlclr-container-elements"></a>STL/CLR 容器項目的需求
插入 STL/CLR 容器的所有參考類型至少必須擁有下列項目：  
  
-   公用的複製建構函式。  
  
-   公用的指派運算子。  
  
-   公用的解構函式。  
  
 此外，關聯的容器，例如[設定](../dotnet/set-stl-clr.md)和[對應](../dotnet/map-stl-clr.md)必須有公用的比較運算子定義，也就是`operator<`預設。 容器的某些作業可能也需要公用預設建構函式和公用等價運算子定義。  
  
 和參考類型一樣，實值類型及要插入一個關聯容器之參考類型的控制代碼必須具有比較運算子，例如 `operator<` 定義。 公用複製建構函式、公用指派運算子和公用解構函式的需求中未包含實值類型或參考類型的控制代碼。  
  
## <a name="see-also"></a>請參閱  
 [C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)