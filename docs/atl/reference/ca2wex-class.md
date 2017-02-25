---
title: "CA2WEX 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATLCONV/CA2WEX"
  - "ATL.CA2WEX"
  - "ATL.CA2WEX<t_nBufferLength>"
  - "ATL::CA2WEX"
  - "ATL::CA2WEX<t_nBufferLength>"
  - "CA2WEX"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CA2WEX 類別"
ms.assetid: 317d9ffb-e84f-47e8-beda-57e28fb19124
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CA2WEX 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

字串轉換巨集使用這個類別 `CA2TEX`、 `CA2CTEX`、 `CT2WEX`和 `CT2CWEX`和 typedef **CA2W**。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
      template<  
int t_nBufferLength= 128  
>  
class CA2WEX  
```  
  
#### 參數  
 `t_nBufferLength`  
 用來轉換程序的緩衝區大小。  預設長度為 128 個位元組。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CA2WEX::CA2WEX](../Topic/CA2WEX::CA2WEX.md)|建構函式。|  
|[CA2WEX::~CA2WEX](../Topic/CA2WEX::~CA2WEX.md)|解構函式。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CA2WEX::operator LPWSTR](../Topic/CA2WEX::operator%20LPWSTR.md)|轉換運算子。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CA2WEX::m\_psz](../Topic/CA2WEX::m_psz.md)|儲存來源字串的資料成員。|  
|[CA2WEX::m\_szBuffer](../Topic/CA2WEX::m_szBuffer.md)|靜態緩衝區，用來存放已轉換的字串。|  
  
## 備註  
 除非需要額外的功能，請使用 `CA2TEX`， `CA2CTEX`、 `CT2WEX`、 `CT2CWEX`或 **CA2W** 在您的程式碼。  
  
 這個類別包含用來儲存轉換結果的固定大小的靜態緩衝區。  如果結果太大而無法符合這個靜態緩衝區，使用 `malloc`，類別配置記憶體，釋放記憶體，當物件超出範圍時。  這可確保不同，文字轉換巨集有 ATL 舊版中，這個類別是安全使用迴圈，並不會讓堆疊溢位。  
  
 如果類別嘗試在堆積上配置記憶體而失敗時，便會呼叫與 **E\_OUTOFMEMORY**引數的 `AtlThrow` 。  
  
 根據預設， ATL 轉換類別和巨集來轉換使用目前執行緒的 ANSI 字碼頁。  如果您要覆寫特定轉換的該行為，請指定字碼頁做為第二個參數傳遞給建構函式的類別。  
  
 下列巨集以此類別:  
  
-   `CA2TEX`  
  
-   `CA2CTEX`  
  
-   `CT2WEX`  
  
-   `CT2CWEX`  
  
 下列 typedef 依據此類別:  
  
-   **CA2 W**  
  
 如需這些的討論文字轉換巨集，請參閱 [ATL 和 MFC 字串轉換巨集](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md)。  
  
## 範例  
 針對使用這類字串轉換巨集參閱 [ATL 和 MFC 字串轉換巨集](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md) 。  
  
## 需求  
 **Header:** atlconv.h  
  
## 請參閱  
 [CA2AEX 類別](../../atl/reference/ca2aex-class.md)   
 [CA2CAEX 類別](../../atl/reference/ca2caex-class.md)   
 [CW2AEX 類別](../../atl/reference/cw2aex-class.md)   
 [CW2CWEX 類別](../../atl/reference/cw2cwex-class.md)   
 [CW2WEX 類別](../../atl/reference/cw2wex-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)