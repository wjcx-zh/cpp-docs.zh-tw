---
title: "32 位元 Windows 日期/時間格式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.time
dev_langs:
- C++
helpviewer_keywords:
- 32-bit Windows
ms.assetid: ef1589db-84d7-4b24-8799-7c7a22cfe2bf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 20e812a1eca6e620e0c1847b6ea6a07b871a407d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="32-bit-windows-timedate-formats"></a>32 位元 Windows 日期/時間格式
使用不帶正負號整數作為位元欄位，來個別儲存檔案時間和日期。 檔案時間和日期會封裝如下︰  
  
### <a name="time"></a>時間  
  
|位元位置︰|0   1   2   3   4|5   6   7   8   9   A|B   C   D   E   F|  
|-------------------|-----------------------|---------------------------|-----------------------|  
|長度：|5|6|5|  
|內容: |小時|分鐘|2 秒增量|  
|數值範圍：|0-23|0-59|2 秒間隔內為 0-29|  
  
### <a name="date"></a>Date  
  
|位元位置︰|0   1   2   3   4   5   6|7   8   9   A|B   C   D   E   F|  
|-------------------|-------------------------------|-------------------|-----------------------|  
|長度：|7|4|5|  
|內容: |年|月|天|  
|數值範圍：|0-119|1-12|1-31|  
||(相對於 1980)|||  
  
## <a name="see-also"></a>請參閱  
 [全域常數](../c-runtime-library/global-constants.md)