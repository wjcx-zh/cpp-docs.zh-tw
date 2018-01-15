---
title: "OpenMP 程式庫 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: f89abf97-67e3-4327-bc30-43f85b9533a2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5c0f009c26789fd771d55dab5fcfe5f342aa03b1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="openmp-libraries"></a>OpenMP 程式庫
討論在 Visual c + + 中的 OpenMP 執行階段程式庫所組成的.lib 檔案。  
  
 下列程式庫包含 Visual c + + OpenMP 執行階段程式庫函式。  
  
|OpenMP 執行階段程式庫|特性|  
|------------------------------|---------------------|  
|VCOMP。LIB|多執行緒、 動態連結 （如 VCOMP 匯入程式庫。LIB)。|  
|VCOMPD。LIB|多執行緒、 動態連結 （如 VCOMPD 匯入程式庫。筆記電腦螢幕） （偵錯）|  
  
 如果在編譯中定義了 _DEBUG 而且`#include omp.h`原始程式碼 VCOMPD 中。LIB 將預設程式庫。 否則，VCOMP。將會使用 LIB。  
  
 您可以使用[/NODEFAULTLIB （忽略程式庫）](../../../build/reference/nodefaultlib-ignore-libraries.md)移除預設程式庫，並明確地連結您所選擇的程式庫。  
  
 OpenMP Dll Visual c + + 可轉散發套件目錄中，而且需要使用 OpenMP 應用程式一起散發。  
  
## <a name="see-also"></a>請參閱  
 [程式庫參考](../../../parallel/openmp/reference/openmp-library-reference.md)