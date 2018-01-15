---
title: "程式庫 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: LIBRARY
dev_langs: C++
helpviewer_keywords: LIBRARY .def file statement
ms.assetid: 1d7ccc92-e088-4ef7-9ef0-25c3862cc051
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 71637c83eda0ee641a4b66d94ba113162baa7bf2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="library"></a>LIBRARY
會告知連結來建立 DLL。 同時，連結會建立匯入程式庫，除非在組建中使用.exp 檔。  
  
```  
LIBRARY [library][BASE=address]  
```  
  
## <a name="remarks"></a>備註  
 *文件庫*引數指定的 DLL 名稱。 您也可以使用[/out](../../build/reference/out-output-file-name.md)連結器選項來指定 DLL 的輸出名稱。  
  
 基底 =*位址*引數則設定作業系統使用載入的 DLL 的基底位址。 這個引數會覆寫 0x10000000 預設 DLL 位置。 請參閱描述[/基底](../../build/reference/base-base-address.md)基底地址的詳細資料的選項。  
  
 請務必使用[/DLL](../../build/reference/dll-build-a-dll.md)連結器選項，當您建置 DLL。  
  
## <a name="see-also"></a>請參閱  
 [模組定義陳述式的規則](../../build/reference/rules-for-module-definition-statements.md)