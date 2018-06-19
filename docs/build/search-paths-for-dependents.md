---
title: 相依的搜尋路徑 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, dependents
- dependents, NMAKE
ms.assetid: bf998e47-da74-48b5-891d-d3d8ce57264b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 577fc7e44bfff35cf7efdcff20dc4cdca1c7001e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380481"
---
# <a name="search-paths-for-dependents"></a>相依的搜尋路徑
每個相依都有選擇性的搜尋路徑，指定方式如下：  
  
## <a name="syntax"></a>語法  
  
```  
{directory[;directory...]}dependent  
```  
  
## <a name="remarks"></a>備註  
 NMAKE 會尋找第一次在目前目錄中，然後在目錄中指定的順序相依性。 部分或全部的搜尋路徑，可以指定巨集。 將目錄名稱括在大括號 （{}）;以分號 （;） 分隔多個目錄。 不允許任何空格或定位字元。  
  
## <a name="see-also"></a>另請參閱  
 [相依性](../build/dependents.md)