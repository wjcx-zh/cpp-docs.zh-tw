---
title: "PogoSafeMode |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: PogoSafeMode
ms.assetid: 2daeeff7-44cb-417f-90eb-6b9edf658533
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5f40dad6feff9e49deeb495e8acbf2584dea3e41
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="pogosafemode"></a>PogoSafeMode
指定要用於快速模式或 「 安全模式的應用程式分析。  
  
## <a name="syntax"></a>語法  
  
```  
PogoSafeMode  
```  
  
## <a name="remarks"></a>備註  
 特性指引最佳化 (PGO) 的程式碼剖析工作階段有兩個可能的模式： 快速模式和安全模式。 當程式碼剖析為快速模式時，它會使用**INC**指令，以便增加資料計數器。 **INC**指令更快，但不是安全執行緒。 當程式碼剖析處於安全模式時，它會使用**鎖定 INC**指令，以便增加資料計數器。 **鎖定 INC**指令具有相同的功能**INC**指令，且具備執行緒安全，但是它低於**INC**指令。  
  
 根據預設，PGO 分析在快速模式下運作。 `PogoSafeMode`是如果您想要使用安全模式，才需要。  
  
 若要執行 PGO 分析在安全模式中，您必須使用環境變數`PogoSafeMode`或連結器參數**-PogoSafeMode**，取決於系統上。 如果您正在執行分析在 x64 電腦，您必須使用連結器參數。 如果您正在執行 x86 程式碼剖析的電腦，您必須定義環境變數的任何值之前啟動最佳化處理序。  
  
## <a name="example"></a>範例  
  
```  
set PogoSafeMode=1  
```  
  
## <a name="see-also"></a>請參閱  
 [特性指引最佳化的環境變數](../../build/reference/environment-variables-for-profile-guided-optimizations.md)   
 [特性指引最佳化](../../build/reference/profile-guided-optimizations.md)