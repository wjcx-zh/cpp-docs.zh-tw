---
title: "32 位元 Windows 日期/時間格式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.time"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "32 位元 Windows"
ms.assetid: ef1589db-84d7-4b24-8799-7c7a22cfe2bf
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 32 位元 Windows 日期/時間格式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

檔案時間和日期個別儲存，使用不帶正負號的整數當做位元欄位。  封裝檔案時間和日期如下:  
  
### Time  
  
|位元位置:|0   1   2   3   4|5   6   7   8   9   A|B   C   D   E   F|  
|-----------|-----------------------|---------------------------|-----------------------|  
|長度:|5|6|5|  
|內容:|hours|minutes|增加 2 秒|  
|數值範圍:|0–23|0–59|0\-29 在 2 秒間隔|  
  
### 日期  
  
|位元位置:|0   1   2   3   4   5   6|7   8   9   A|B   C   D   E   F|  
|-----------|-------------------------------|-------------------|-----------------------|  
|長度:|7|4|5|  
|內容:|year|month|天|  
|數值範圍:|0–119|1–12|1–31|  
||\(相對於 1980\)|||  
  
## 請參閱  
 [全域常數](../c-runtime-library/global-constants.md)