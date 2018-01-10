---
title: "相依的搜尋路徑 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, dependents
- dependents, NMAKE
ms.assetid: bf998e47-da74-48b5-891d-d3d8ce57264b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f6093db4ac8e0c88dfe6e4b5a5463e5ee8d24349
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="search-paths-for-dependents"></a>相依的搜尋路徑
每個相依都有選擇性的搜尋路徑，指定方式如下：  
  
## <a name="syntax"></a>語法  
  
```  
{directory[;directory...]}dependent  
```  
  
## <a name="remarks"></a>備註  
 NMAKE 會尋找第一次在目前目錄中，然後在目錄中指定的順序相依性。 部分或全部的搜尋路徑，可以指定巨集。 將目錄名稱括在大括號 （{}）;以分號 （;） 分隔多個目錄。 不允許任何空格或定位字元。  
  
## <a name="see-also"></a>請參閱  
 [相依性](../build/dependents.md)