---
title: "CW2AEX 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CW2AEX<t_nBufferLength>"
  - "CW2AEX"
  - "ATL.CW2AEX<t_nBufferLength>"
  - "ATL::CW2AEX"
  - "ATL.CW2AEX"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CW2AEX 類別"
ms.assetid: 44dc2cf5-dd30-440b-a9b9-b21b43f49843
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CW2AEX 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

字串轉換巨集使用這個類別 `CT2AEX`、 `CW2TEX`、 `CW2CTEX`和 `CT2CAEX`和 typedef **CW2A**。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
      template<  
int t_nBufferLength= 128  
>  
class CW2AEX  
```  
  
#### 參數  
 `t_nBufferLength`  
 用來轉換程序的緩衝區大小。  預設長度為 128 個位元組。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CW2AEX::CW2AEX](../Topic/CW2AEX::CW2AEX.md)|建構函式。|  
|[CW2AEX::~CW2AEX](../Topic/CW2AEX::~CW2AEX.md)|解構函式。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CW2AEX::operator LPSTR](../Topic/CW2AEX::operator%20LPSTR.md)|轉換運算子。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CW2AEX::m\_psz](../Topic/CW2AEX::m_psz.md)|儲存來源字串的資料成員。|  
|[CW2AEX::m\_szBuffer](../Topic/CW2AEX::m_szBuffer.md)|靜態緩衝區，用來存放已轉換的字串。|  
  
## 備註  
 除非需要額外的功能，請使用 `CT2AEX`， `CW2TEX`、 `CW2CTEX`、 `CT2CAEX`或 **CW2A** 在您的程式碼。  
  
 這個類別包含用來儲存轉換結果的固定大小的靜態緩衝區。  如果結果太大而無法符合這個靜態緩衝區，使用 `malloc`，類別配置記憶體，釋放記憶體，當物件超出範圍時。  這可確保不同，文字轉換巨集有 ATL 舊版中，這個類別是安全使用迴圈，並不會讓堆疊溢位。  
  
 如果類別嘗試在堆積上配置記憶體而失敗時，便會呼叫與 **E\_OUTOFMEMORY**引數的 `AtlThrow` 。  
  
 根據預設， ATL 轉換類別和巨集來轉換使用目前執行緒的 ANSI 字碼頁。  如果您要覆寫特定轉換的該行為，請指定字碼頁做為第二個參數傳遞給建構函式的類別。  
  
 下列巨集以此類別:  
  
-   `CT2AEX`  
  
-   `CW2TEX`  
  
-   `CW2CTEX`  
  
-   `CT2CAEX`  
  
 下列 typedef 依據此類別:  
  
-   **CW2。**  
  
 如需這些的討論文字轉換巨集，請參閱 [ATL 和 MFC 字串轉換巨集](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md)。  
  
## 範例  
 針對使用這類字串轉換巨集參閱 [ATL 和 MFC 字串轉換巨集](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md) 。  
  
## 需求  
 **Header:** atlconv.h  
  
## 請參閱  
 [CA2AEX 類別](../../atl/reference/ca2aex-class.md)   
 [CA2CAEX 類別](../../atl/reference/ca2caex-class.md)   
 [CA2WEX 類別](../../atl/reference/ca2wex-class.md)   
 [CW2CWEX 類別](../../atl/reference/cw2cwex-class.md)   
 [CW2WEX 類別](../../atl/reference/cw2wex-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)