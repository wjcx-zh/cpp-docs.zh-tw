---
title: x86 內建函式清單
description: Microsoft C++編譯器在 Visual Studio 中支援的 x64 (AMD64) 內部函數的參考清單。
ms.date: 02/28/2020
f1_keywords:
- intrin/_addcarry_u16
- intrin/_addcarry_u32
- intrin/_addcarry_u8
- immintrin/_addcarryx_u32
- ammintrin/_andn_u32
- ammintrin/_bextr_u32
- ammintrin/_bextri_u32
- ammintrin/_blcfill_u32
- ammintrin/_blci_u32
- ammintrin/_blcic_u32
- ammintrin/_blcmsk_u32
- ammintrin/_blcs_u32
- ammintrin/_blsfill_u32
- ammintrin/_blsi_u32
- ammintrin/_blsic_u32
- ammintrin/_blsmsk_u32
- ammintrin/_blsr_u32
- immintrin/_bzhi_u32
- intrin/_clac
- immintrin/_fxrstor
- immintrin/_fxsave
- immintrin/_invpcid
- intrin/_lgdt
- immintrin/_load_be_u16
- immintrin/_loadbe_i16
- immintrin/_load_be_u32
- immintrin/_loadbe_i32
- ammintrin/__llwpcb
- ammintrin/__lwpins32
- ammintrin/__lwpval32
- ammintrin/_lzcnt_u32
- intrin/_m_empty
- intrin/_m_femms
- intrin/_m_from_float
- intrin/_m_from_int
- intrin/_m_maskmovq
- intrin/_m_packssdw
- intrin/_m_packsswb
- intrin/_m_packuswb
- intrin/_m_paddb
- intrin/_m_paddd
- intrin/_m_paddsb
- intrin/_m_paddsw
- intrin/_m_paddusb
- intrin/_m_paddusw
- intrin/_m_paddw
- intrin/_m_pand
- intrin/_m_pandn
- intrin/_m_pavgb
- intrin/_m_pavgusb
- intrin/_m_pavgw
- intrin/_m_pcmpeqb
- intrin/_m_pcmpeqd
- intrin/_m_pcmpeqw
- intrin/_m_pcmpgtb
- intrin/_m_pcmpgtd
- intrin/_m_pcmpgtw
- intrin/_m_pextrw
- intrin/_m_pf2id
- intrin/_m_pf2iw
- intrin/_m_pfacc
- intrin/_m_pfadd
- intrin/_m_pfcmpeq
- intrin/_m_pfcmpge
- intrin/_m_pfcmpgt
- intrin/_m_pfmax
- intrin/_m_pfmin
- intrin/_m_pfmul
- intrin/_m_pfnacc
- intrin/_m_pfpnacc
- intrin/_m_pfrcp
- intrin/_m_pfrcpit1
- intrin/_m_pfrcpit2
- intrin/_m_pfrsqit1
- intrin/_m_pfrsqrt
- intrin/_m_pfsub
- intrin/_m_pfsubr
- intrin/_m_pi2fd
- intrin/_m_pi2fw
- intrin/_m_pinsrw
- intrin/_m_pmaddwd
- intrin/_m_pmaxsw
- intrin/_m_pmaxub
- intrin/_m_pminsw
- intrin/_m_pminub
- intrin/_m_pmovmskb
- intrin/_m_pmulhrw
- intrin/_m_pmulhuw
- intrin/_m_pmulhw
- intrin/_m_pmullw
- intrin/_m_por
- intrin/_m_prefetch
- intrin/_m_prefetchw
- intrin/_m_psadbw
- intrin/_m_pshufw
- intrin/_m_pslld
- intrin/_m_pslldi
- intrin/_m_psllq
- intrin/_m_psllqi
- intrin/_m_psllw
- intrin/_m_psllwi
- intrin/_m_psrad
- intrin/_m_psradi
- intrin/_m_psraw
- intrin/_m_psrawi
- intrin/_m_psrld
- intrin/_m_psrldi
- intrin/_m_psrlq
- intrin/_m_psrlqi
- intrin/_m_psrlw
- intrin/_m_psrlwi
- intrin/_m_psubb
- intrin/_m_psubd
- intrin/_m_psubsb
- intrin/_m_psubsw
- intrin/_m_psubusb
- intrin/_m_psubusw
- intrin/_m_psubw
- intrin/_m_pswapd
- intrin/_m_punpckhbw
- intrin/_m_punpckhdq
- intrin/_m_punpckhwd
- intrin/_m_punpcklbw
- intrin/_m_punpckldq
- intrin/_m_punpcklwd
- intrin/_m_pxor
- intrin/_m_to_float
- intrin/_m_to_int
- intrin/_mm_abs_epi16
- intrin/_mm_abs_epi32
- intrin/_mm_abs_epi8
- intrin/_mm_abs_pi16
- intrin/_mm_abs_pi32
- intrin/_mm_abs_pi8
- intrin/_mm_add_epi16
- intrin/_mm_add_epi32
- intrin/_mm_add_epi64
- intrin/_mm_add_epi8
- intrin/_mm_add_pd
- mmintrin/_mm_add_pi8
- mmintrin/_mm_add_pi16
- mmintrin/_mm_add_pi32
- intrin/_mm_add_ps
- intrin/_mm_add_sd
- intrin/_mm_add_si64
- intrin/_mm_add_ss
- intrin/_mm_adds_epi16
- intrin/_mm_adds_epi8
- intrin/_mm_adds_epu16
- intrin/_mm_adds_epu8
- mmintrin/_mm_adds_pi8
- mmintrin/_mm_adds_pi16
- mmintrin/_mm_adds_pu8
- mmintrin/_mm_adds_pu16
- intrin/_mm_addsub_pd
- intrin/_mm_addsub_ps
- immintrin/_mm_aesdec_si128
- immintrin/_mm_aesdeclast_si128
- immintrin/_mm_aesenc_si128
- immintrin/_mm_aesenclast_si128
- immintrin/_mm_aesimc_si128
- immintrin/_mm_aeskeygenassist_si128
- intrin/_mm_alignr_epi8
- intrin/_mm_alignr_pi8
- intrin/_mm_and_pd
- intrin/_mm_and_ps
- mmintrin/_mm_and_si64
- intrin/_mm_and_si128
- intrin/_mm_andnot_pd
- intrin/_mm_andnot_ps
- mmintrin/_mm_andnot_si64
- intrin/_mm_andnot_si128
- intrin/_mm_avg_epu16
- intrin/_mm_avg_epu8
- intrin/_mm_blend_epi16
- immintrin/_mm_blend_epi32
- intrin/_mm_blend_pd
- intrin/_mm_blend_ps
- intrin/_mm_blendv_epi8
- intrin/_mm_blendv_pd
- intrin/_mm_blendv_ps
- immintrin/_mm_broadcast_ss
- immintrin/_mm_broadcastb_epi8
- immintrin/_mm_broadcastd_epi32
- immintrin/_mm_broadcastq_epi64
- immintrin/_mm_broadcastsd_pd
- immintrin/_mm_broadcastss_ps
- immintrin/_mm_broadcastw_epi16
- intrin/_mm_castpd_ps
- intrin/_mm_castpd_si128
- intrin/_mm_castps_pd
- intrin/_mm_castps_si128
- intrin/_mm_castsi128_pd
- intrin/_mm_castsi128_ps
- intrin/_mm_clflush
- immintrin/_mm_clmulepi64_si128
- ammintrin/_mm_cmov_si128
- immintrin/_mm_cmp_pd
- immintrin/_mm_cmp_ps
- immintrin/_mm_cmp_sd
- immintrin/_mm_cmp_ss
- intrin/_mm_cmpeq_epi16
- intrin/_mm_cmpeq_epi32
- intrin/_mm_cmpeq_epi64
- intrin/_mm_cmpeq_epi8
- intrin/_mm_cmpeq_pd
- mmintrin/_mm_cmpeq_pi8
- mmintrin/_mm_cmpeq_pi16
- mmintrin/_mm_cmpeq_pi32
- intrin/_mm_cmpeq_ps
- intrin/_mm_cmpeq_sd
- intrin/_mm_cmpeq_ss
- intrin/_mm_cmpestra
- intrin/_mm_cmpestrc
- intrin/_mm_cmpestri
- intrin/_mm_cmpestrm
- intrin/_mm_cmpestro
- intrin/_mm_cmpestrs
- intrin/_mm_cmpestrz
- intrin/_mm_cmpge_pd
- intrin/_mm_cmpge_ps
- intrin/_mm_cmpge_sd
- intrin/_mm_cmpge_ss
- intrin/_mm_cmpgt_epi16
- intrin/_mm_cmpgt_epi32
- intrin/_mm_cmpgt_epi64
- intrin/_mm_cmpgt_epi8
- mmintrin/_mm_cmpgt_pi8
- mmintrin/_mm_cmpgt_pi16
- mmintrin/_mm_cmpgt_pi32
- intrin/_mm_cmpgt_pd
- intrin/_mm_cmpgt_ps
- intrin/_mm_cmpgt_sd
- intrin/_mm_cmpgt_ss
- intrin/_mm_cmpistra
- intrin/_mm_cmpistrc
- intrin/_mm_cmpistri
- intrin/_mm_cmpistrm
- intrin/_mm_cmpistro
- intrin/_mm_cmpistrs
- intrin/_mm_cmpistrz
- intrin/_mm_cmple_pd
- intrin/_mm_cmple_ps
- intrin/_mm_cmple_sd
- intrin/_mm_cmple_ss
- intrin/_mm_cmplt_epi16
- intrin/_mm_cmplt_epi32
- intrin/_mm_cmplt_epi8
- intrin/_mm_cmplt_pd
- intrin/_mm_cmplt_ps
- intrin/_mm_cmplt_sd
- intrin/_mm_cmplt_ss
- intrin/_mm_cmpneq_pd
- intrin/_mm_cmpneq_ps
- intrin/_mm_cmpneq_sd
- intrin/_mm_cmpneq_ss
- intrin/_mm_cmpnge_pd
- intrin/_mm_cmpnge_ps
- intrin/_mm_cmpnge_sd
- intrin/_mm_cmpnge_ss
- intrin/_mm_cmpngt_pd
- intrin/_mm_cmpngt_ps
- intrin/_mm_cmpngt_sd
- intrin/_mm_cmpngt_ss
- intrin/_mm_cmpnle_pd
- intrin/_mm_cmpnle_ps
- intrin/_mm_cmpnle_sd
- intrin/_mm_cmpnle_ss
- intrin/_mm_cmpnlt_pd
- intrin/_mm_cmpnlt_ps
- intrin/_mm_cmpnlt_sd
- intrin/_mm_cmpnlt_ss
- intrin/_mm_cmpord_pd
- intrin/_mm_cmpord_ps
- intrin/_mm_cmpord_sd
- intrin/_mm_cmpord_ss
- intrin/_mm_cmpunord_pd
- intrin/_mm_cmpunord_ps
- intrin/_mm_cmpunord_sd
- intrin/_mm_cmpunord_ss
- ammintrin/_mm_com_epi16
- ammintrin/_mm_com_epi32
- ammintrin/_mm_com_epi64
- ammintrin/_mm_com_epi8
- ammintrin/_mm_com_epu16
- ammintrin/_mm_com_epu32
- ammintrin/_mm_com_epu64
- ammintrin/_mm_com_epu8
- intrin/_mm_comieq_sd
- intrin/_mm_comieq_ss
- intrin/_mm_comige_sd
- intrin/_mm_comige_ss
- intrin/_mm_comigt_sd
- intrin/_mm_comigt_ss
- intrin/_mm_comile_sd
- intrin/_mm_comile_ss
- intrin/_mm_comilt_sd
- intrin/_mm_comilt_ss
- intrin/_mm_comineq_sd
- intrin/_mm_comineq_ss
- intrin/_mm_crc32_u16
- intrin/_mm_crc32_u32
- intrin/_mm_crc32_u8
- intrin/_mm_cvt_pi2ps
- intrin/_mm_cvt_ps2pi
- intrin/_mm_cvt_si2ss
- intrin/_mm_cvt_ss2si
- intrin/_mm_cvtepi16_epi32
- intrin/_mm_cvtepi16_epi64
- intrin/_mm_cvtepi32_epi64
- intrin/_mm_cvtepi32_pd
- intrin/_mm_cvtepi32_ps
- intrin/_mm_cvtepi8_epi16
- intrin/_mm_cvtepi8_epi32
- intrin/_mm_cvtepi8_epi64
- intrin/_mm_cvtepu16_epi32
- intrin/_mm_cvtepu16_epi64
- intrin/_mm_cvtepu32_epi64
- intrin/_mm_cvtepu8_epi16
- intrin/_mm_cvtepu8_epi32
- intrin/_mm_cvtepu8_epi64
- intrin/_mm_cvtpd_epi32
- intrin/_mm_cvtpd_pi32
- intrin/_mm_cvtpd_ps
- immintrin/_mm_cvtph_ps
- intrin/_mm_cvtpi32_pd
- intrin/_mm_cvtps_epi32
- intrin/_mm_cvtps_pd
- immintrin/_mm_cvtps_ph
- intrin/_mm_cvtsd_f64
- intrin/_mm_cvtsd_si32
- intrin/_mm_cvtsd_ss
- intrin/_mm_cvtsi128_si32
- intrin/_mm_cvtsi32_sd
- intrin/_mm_cvtsi32_si128
- mmintrin/_mm_cvtsi32_si64
- mmintrin/_mm_cvtsi64_si32
- intrin/_mm_cvtss_f32
- intrin/_mm_cvtss_sd
- intrin/_mm_cvtt_ps2pi
- intrin/_mm_cvtt_ss2si
- intrin/_mm_cvttpd_epi32
- intrin/_mm_cvttpd_pi32
- intrin/_mm_cvttps_epi32
- intrin/_mm_cvttsd_si32
- intrin/_mm_div_pd
- intrin/_mm_div_ps
- intrin/_mm_div_sd
- intrin/_mm_div_ss
- intrin/_mm_dp_pd
- intrin/_mm_dp_ps
- mmintrin/_mm_empty
- intrin/_mm_extract_epi16
- intrin/_mm_extract_epi32
- intrin/_mm_extract_epi8
- intrin/_mm_extract_ps
- immintrin/_mm_fmadd_pd
- immintrin/_mm_fmadd_ps
- immintrin/_mm_fmadd_sd
- immintrin/_mm_fmadd_ss
- immintrin/_mm_fmaddsub_pd
- immintrin/_mm_fmaddsub_ps
- immintrin/_mm_fmsub_pd
- immintrin/_mm_fmsub_ps
- immintrin/_mm_fmsub_sd
- immintrin/_mm_fmsub_ss
- immintrin/_mm_fmsubadd_pd
- immintrin/_mm_fmsubadd_ps
- immintrin/_mm_fnmadd_pd
- immintrin/_mm_fnmadd_ps
- immintrin/_mm_fnmadd_sd
- immintrin/_mm_fnmadd_ss
- immintrin/_mm_fnmsub_pd
- immintrin/_mm_fnmsub_ps
- immintrin/_mm_fnmsub_sd
- immintrin/_mm_fnmsub_ss
- ammintrin/_mm_frcz_pd
- ammintrin/_mm_frcz_ps
- ammintrin/_mm_frcz_sd
- ammintrin/_mm_frcz_ss
- intrin/_mm_getcsr
- intrin/_mm_hadd_epi16
- intrin/_mm_hadd_epi32
- intrin/_mm_hadd_pd
- intrin/_mm_hadd_pi16
- intrin/_mm_hadd_pi32
- intrin/_mm_hadd_ps
- ammintrin/_mm_haddd_epi16
- ammintrin/_mm_haddd_epi8
- ammintrin/_mm_haddd_epu16
- ammintrin/_mm_haddd_epu8
- ammintrin/_mm_haddq_epi16
- ammintrin/_mm_haddq_epi32
- ammintrin/_mm_haddq_epi8
- ammintrin/_mm_haddq_epu16
- ammintrin/_mm_haddq_epu32
- ammintrin/_mm_haddq_epu8
- intrin/_mm_hadds_epi16
- intrin/_mm_hadds_pi16
- ammintrin/_mm_haddw_epi8
- ammintrin/_mm_haddw_epu8
- intrin/_mm_hsub_epi16
- intrin/_mm_hsub_epi32
- intrin/_mm_hsub_pd
- intrin/_mm_hsub_pi16
- intrin/_mm_hsub_pi32
- intrin/_mm_hsub_ps
- ammintrin/_mm_hsubd_epi16
- ammintrin/_mm_hsubq_epi32
- intrin/_mm_hsubs_epi16
- intrin/_mm_hsubs_pi16
- ammintrin/_mm_hsubw_epi8
- immintrin/_mm_i32gather_epi32
- immintrin/_mm_i32gather_epi64
- immintrin/_mm_i32gather_pd
- immintrin/_mm_i32gather_ps
- immintrin/_mm_i64gather_epi32
- immintrin/_mm_i64gather_epi64
- immintrin/_mm_i64gather_pd
- immintrin/_mm_i64gather_ps
- intrin/_mm_insert_epi16
- intrin/_mm_insert_epi32
- intrin/_mm_insert_epi8
- intrin/_mm_insert_ps
- intrin/_mm_lddqu_si128
- intrin/_mm_lfence
- intrin/_mm_load_pd
- intrin/_mm_load_ps
- intrin/_mm_load_ps1
- intrin/_mm_load_sd
- intrin/_mm_load_si128
- intrin/_mm_load_ss
- intrin/_mm_load1_pd
- intrin/_mm_loaddup_pd
- intrin/_mm_loadh_pd
- intrin/_mm_loadh_pi
- intrin/_mm_loadl_epi64
- intrin/_mm_loadl_pd
- intrin/_mm_loadl_pi
- intrin/_mm_loadr_pd
- intrin/_mm_loadr_ps
- intrin/_mm_loadu_pd
- intrin/_mm_loadu_ps
- intrin/_mm_loadu_si128
- ammintrin/_mm_macc_epi16
- ammintrin/_mm_macc_epi32
- ammintrin/_mm_macc_pd
- ammintrin/_mm_macc_ps
- ammintrin/_mm_macc_sd
- ammintrin/_mm_macc_ss
- ammintrin/_mm_maccd_epi16
- ammintrin/_mm_macchi_epi32
- ammintrin/_mm_macclo_epi32
- ammintrin/_mm_maccs_epi16
- ammintrin/_mm_maccs_epi32
- ammintrin/_mm_maccsd_epi16
- ammintrin/_mm_maccshi_epi32
- ammintrin/_mm_maccslo_epi32
- intrin/_mm_madd_epi16
- mmintrin/_mm_madd_pi16
- ammintrin/_mm_maddd_epi16
- ammintrin/_mm_maddsd_epi16
- ammintrin/_mm_maddsub_pd
- ammintrin/_mm_maddsub_ps
- intrin/_mm_maddubs_epi16
- intrin/_mm_maddubs_pi16
- immintrin/_mm_mask_i32gather_epi32
- immintrin/_mm_mask_i32gather_epi64
- immintrin/_mm_mask_i32gather_pd
- immintrin/_mm_mask_i32gather_ps
- immintrin/_mm_mask_i64gather_epi32
- immintrin/_mm_mask_i64gather_epi64
- immintrin/_mm_mask_i64gather_pd
- immintrin/_mm_mask_i64gather_ps
- immintrin/_mm_maskload_epi32
- immintrin/_mm_maskload_epi64
- immintrin/_mm_maskload_pd
- immintrin/_mm_maskload_ps
- intrin/_mm_maskmoveu_si128
- immintrin/_mm_maskstore_epi32
- immintrin/_mm_maskstore_epi64
- immintrin/_mm_maskstore_pd
- immintrin/_mm_maskstore_ps
- intrin/_mm_max_epi16
- intrin/_mm_max_epi32
- intrin/_mm_max_epi8
- intrin/_mm_max_epu16
- intrin/_mm_max_epu32
- intrin/_mm_max_epu8
- intrin/_mm_max_pd
- intrin/_mm_max_ps
- intrin/_mm_max_sd
- intrin/_mm_max_ss
- intrin/_mm_mfence
- intrin/_mm_min_epi16
- intrin/_mm_min_epi32
- intrin/_mm_min_epi8
- intrin/_mm_min_epu16
- intrin/_mm_min_epu32
- intrin/_mm_min_epu8
- intrin/_mm_min_pd
- intrin/_mm_min_ps
- intrin/_mm_min_sd
- intrin/_mm_min_ss
- intrin/_mm_minpos_epu16
- intrin/_mm_monitor
- intrin/_mm_move_epi64
- intrin/_mm_move_sd
- intrin/_mm_move_ss
- intrin/_mm_movedup_pd
- intrin/_mm_movehdup_ps
- intrin/_mm_movehl_ps
- intrin/_mm_moveldup_ps
- intrin/_mm_movelh_ps
- intrin/_mm_movemask_epi8
- intrin/_mm_movemask_pd
- intrin/_mm_movemask_ps
- intrin/_mm_movepi64_pi64
- intrin/_mm_movpi64_epi64
- intrin/_mm_mpsadbw_epu8
- ammintrin/_mm_msub_pd
- ammintrin/_mm_msub_ps
- ammintrin/_mm_msub_sd
- ammintrin/_mm_msub_ss
- ammintrin/_mm_msubadd_pd
- ammintrin/_mm_msubadd_ps
- intrin/_mm_mul_epi32
- intrin/_mm_mul_epu32
- intrin/_mm_mul_pd
- intrin/_mm_mul_ps
- intrin/_mm_mul_sd
- intrin/_mm_mul_ss
- intrin/_mm_mul_su32
- intrin/_mm_mulhi_epi16
- intrin/_mm_mulhi_epu16
- mmintrin/_mm_mulhi_pi16
- intrin/_mm_mulhrs_epi16
- intrin/_mm_mulhrs_pi16
- intrin/_mm_mullo_epi16
- intrin/_mm_mullo_epi32
- mmintrin/_mm_mullo_pi16
- intrin/_mm_mwait
- ammintrin/_mm_nmacc_pd
- ammintrin/_mm_nmacc_ps
- ammintrin/_mm_nmacc_sd
- ammintrin/_mm_nmacc_ss
- ammintrin/_mm_nmsub_pd
- ammintrin/_mm_nmsub_ps
- ammintrin/_mm_nmsub_sd
- ammintrin/_mm_nmsub_ss
- intrin/_mm_or_pd
- intrin/_mm_or_ps
- mmintrin/_mm_or_si64
- intrin/_mm_or_si128
- intrin/_mm_packs_epi16
- intrin/_mm_packs_epi32
- mmintrin/_mm_packs_pi16
- mmintrin/_mm_packs_pi32
- mmintrin/_mm_packs_pu16
- intrin/_mm_packus_epi16
- intrin/_mm_packus_epi32
- intrin/_mm_pause
- ammintrin/_mm_perm_epi8
- immintrin/_mm_permute_pd
- immintrin/_mm_permute_ps
- ammintrin/_mm_permute2_pd
- ammintrin/_mm_permute2_ps
- immintrin/_mm_permutevar_pd
- immintrin/_mm_permutevar_ps
- intrin/_mm_popcnt_u32
- intrin/_mm_prefetch
- intrin/_mm_rcp_ps
- intrin/_mm_rcp_ss
- ammintrin/_mm_rot_epi16
- ammintrin/_mm_rot_epi32
- ammintrin/_mm_rot_epi64
- ammintrin/_mm_rot_epi8
- ammintrin/_mm_roti_epi16
- ammintrin/_mm_roti_epi32
- ammintrin/_mm_roti_epi64
- ammintrin/_mm_roti_epi8
- intrin/_mm_round_pd
- intrin/_mm_round_ps
- intrin/_mm_round_sd
- intrin/_mm_round_ss
- intrin/_mm_rsqrt_ps
- intrin/_mm_rsqrt_ss
- intrin/_mm_sad_epu8
- intrin/_mm_set_epi16
- intrin/_mm_set_epi32
- intrin/_mm_set_epi64
- intrin/_mm_set_epi8
- intrin/_mm_set_pd
- intrin/_mm_set_pi16
- intrin/_mm_set_pi32
- intrin/_mm_set_pi8
- intrin/_mm_set_ps
- intrin/_mm_set_ps1
- intrin/_mm_set_sd
- intrin/_mm_set_ss
- intrin/_mm_set1_epi16
- intrin/_mm_set1_epi32
- intrin/_mm_set1_epi64
- intrin/_mm_set1_epi8
- intrin/_mm_set1_pd
- intrin/_mm_set1_pi16
- intrin/_mm_set1_pi32
- intrin/_mm_set1_pi8
- intrin/_mm_setcsr
- intrin/_mm_setl_epi64
- intrin/_mm_setr_epi16
- intrin/_mm_setr_epi32
- intrin/_mm_setr_epi64
- intrin/_mm_setr_epi8
- intrin/_mm_setr_pd
- intrin/_mm_setr_pi16
- intrin/_mm_setr_pi32
- intrin/_mm_setr_pi8
- intrin/_mm_setr_ps
- intrin/_mm_setzero_pd
- intrin/_mm_setzero_ps
- intrin/_mm_setzero_si128
- intrin/_mm_setzero_si64
- intrin/_mm_sfence
- ammintrin/_mm_sha_epi16
- ammintrin/_mm_sha_epi32
- ammintrin/_mm_sha_epi64
- ammintrin/_mm_sha_epi8
- ammintrin/_mm_shl_epi16
- ammintrin/_mm_shl_epi32
- ammintrin/_mm_shl_epi64
- ammintrin/_mm_shl_epi8
- intrin/_mm_shuffle_epi32
- intrin/_mm_shuffle_epi8
- intrin/_mm_shuffle_pd
- intrin/_mm_shuffle_pi8
- intrin/_mm_shuffle_ps
- intrin/_mm_shufflehi_epi16
- intrin/_mm_shufflelo_epi16
- intrin/_mm_sign_epi16
- intrin/_mm_sign_epi32
- intrin/_mm_sign_epi8
- intrin/_mm_sign_pi16
- intrin/_mm_sign_pi32
- intrin/_mm_sign_pi8
- intrin/_mm_sll_epi16
- intrin/_mm_sll_epi32
- intrin/_mm_sll_epi64
- mmintrin/_mm_sll_pi16
- mmintrin/_mm_sll_pi32
- mmintrin/_mm_sll_si64
- intrin/_mm_slli_epi16
- intrin/_mm_slli_epi32
- intrin/_mm_slli_epi64
- mmintrin/_mm_slli_pi16
- mmintrin/_mm_slli_pi32
- mmintrin/_mm_slli_si64
- intrin/_mm_slli_si128
- immintrin/_mm_sllv_epi32
- immintrin/_mm_sllv_epi64
- intrin/_mm_sqrt_pd
- intrin/_mm_sqrt_ps
- intrin/_mm_sqrt_sd
- intrin/_mm_sqrt_ss
- intrin/_mm_sra_epi16
- intrin/_mm_sra_epi32
- mmintrin/_mm_sra_pi16
- mmintrin/_mm_sra_pi32
- intrin/_mm_srai_epi16
- intrin/_mm_srai_epi32
- mmintrin/_mm_srai_pi16
- mmintrin/_mm_srai_pi32
- immintrin/_mm_srav_epi32
- intrin/_mm_srl_epi16
- intrin/_mm_srl_epi32
- intrin/_mm_srl_epi64
- mmintrin/_mm_srl_pi16
- mmintrin/_mm_srl_pi32
- mmintrin/_mm_srl_si64
- intrin/_mm_srli_epi16
- intrin/_mm_srli_epi32
- intrin/_mm_srli_epi64
- mmintrin/_mm_srli_pi16
- mmintrin/_mm_srli_pi32
- mmintrin/_mm_srli_si64
- intrin/_mm_srli_si128
- immintrin/_mm_srlv_epi32
- immintrin/_mm_srlv_epi64
- intrin/_mm_store_pd
- intrin/_mm_store_ps
- intrin/_mm_store_ps1
- intrin/_mm_store_sd
- intrin/_mm_store_si128
- intrin/_mm_store_ss
- intrin/_mm_store1_pd
- intrin/_mm_storeh_pd
- intrin/_mm_storeh_pi
- intrin/_mm_storel_epi64
- intrin/_mm_storel_pd
- intrin/_mm_storel_pi
- intrin/_mm_storer_pd
- intrin/_mm_storer_ps
- intrin/_mm_storeu_pd
- intrin/_mm_storeu_ps
- intrin/_mm_storeu_si128
- intrin/_mm_stream_load_si128
- intrin/_mm_stream_pd
- intrin/_mm_stream_pi
- intrin/_mm_stream_ps
- intrin/_mm_stream_si128
- intrin/_mm_stream_si32
- intrin/_mm_sub_epi16
- intrin/_mm_sub_epi32
- intrin/_mm_sub_epi64
- intrin/_mm_sub_epi8
- intrin/_mm_sub_pd
- mmintrin/_mm_sub_pi8
- mmintrin/_mm_sub_pi16
- mmintrin/_mm_sub_pi32
- intrin/_mm_sub_ps
- intrin/_mm_sub_sd
- intrin/_mm_sub_si64
- intrin/_mm_sub_ss
- intrin/_mm_subs_epi16
- intrin/_mm_subs_epi8
- intrin/_mm_subs_epu16
- intrin/_mm_subs_epu8
- mmintrin/_mm_subs_pi8
- mmintrin/_mm_subs_pi16
- mmintrin/_mm_subs_pu8
- mmintrin/_mm_subs_pu16
- immintrin/_mm_testc_pd
- immintrin/_mm_testc_ps
- intrin/_mm_testc_si128
- immintrin/_mm_testnzc_pd
- immintrin/_mm_testnzc_ps
- intrin/_mm_testnzc_si128
- immintrin/_mm_testz_pd
- immintrin/_mm_testz_ps
- intrin/_mm_testz_si128
- intrin/_mm_ucomieq_sd
- intrin/_mm_ucomieq_ss
- intrin/_mm_ucomige_sd
- intrin/_mm_ucomige_ss
- intrin/_mm_ucomigt_sd
- intrin/_mm_ucomigt_ss
- intrin/_mm_ucomile_sd
- intrin/_mm_ucomile_ss
- intrin/_mm_ucomilt_sd
- intrin/_mm_ucomilt_ss
- intrin/_mm_ucomineq_sd
- intrin/_mm_ucomineq_ss
- intrin/_mm_unpackhi_epi16
- intrin/_mm_unpackhi_epi32
- intrin/_mm_unpackhi_epi64
- intrin/_mm_unpackhi_epi8
- intrin/_mm_unpackhi_pd
- mmintrin/_mm_unpackhi_pi8
- mmintrin/_mm_unpackhi_pi16
- mmintrin/_mm_unpackhi_pi32
- intrin/_mm_unpackhi_ps
- intrin/_mm_unpacklo_epi16
- intrin/_mm_unpacklo_epi32
- intrin/_mm_unpacklo_epi64
- intrin/_mm_unpacklo_epi8
- intrin/_mm_unpacklo_pd
- mmintrin/_mm_unpacklo_pi8
- mmintrin/_mm_unpacklo_pi16
- mmintrin/_mm_unpacklo_pi32
- intrin/_mm_unpacklo_ps
- intrin/_mm_xor_pd
- intrin/_mm_xor_ps
- mmintrin/_mm_xor_si64
- intrin/_mm_xor_si128
- immintrin/_mm256_abs_epi16
- immintrin/_mm256_abs_epi32
- immintrin/_mm256_abs_epi8
- immintrin/_mm256_add_epi16
- immintrin/_mm256_add_epi32
- immintrin/_mm256_add_epi64
- immintrin/_mm256_add_epi8
- immintrin/_mm256_add_pd
- immintrin/_mm256_add_ps
- immintrin/_mm256_adds_epi16
- immintrin/_mm256_adds_epi8
- immintrin/_mm256_adds_epu16
- immintrin/_mm256_adds_epu8
- immintrin/_mm256_addsub_pd
- immintrin/_mm256_addsub_ps
- immintrin/_mm256_alignr_epi8
- immintrin/_mm256_and_pd
- immintrin/_mm256_and_ps
- immintrin/_mm256_and_si256
- immintrin/_mm256_andnot_pd
- immintrin/_mm256_andnot_ps
- immintrin/_mm256_andnot_si256
- immintrin/_mm256_avg_epu16
- immintrin/_mm256_avg_epu8
- immintrin/_mm256_blend_epi16
- immintrin/_mm256_blend_epi32
- immintrin/_mm256_blend_pd
- immintrin/_mm256_blend_ps
- immintrin/_mm256_blendv_epi8
- immintrin/_mm256_blendv_pd
- immintrin/_mm256_blendv_ps
- immintrin/_mm256_broadcast_pd
- immintrin/_mm256_broadcast_ps
- immintrin/_mm256_broadcast_sd
- immintrin/_mm256_broadcast_ss
- immintrin/_mm256_broadcastb_epi8
- immintrin/_mm256_broadcastd_epi32
- immintrin/_mm256_broadcastq_epi64
- immintrin/_mm256_broadcastsd_pd
- immintrin/_mm256_broadcastsi128_si256
- immintrin/_mm256_broadcastss_ps
- immintrin/_mm256_broadcastw_epi16
- immintrin/_mm256_castpd_ps
- immintrin/_mm256_castpd_si256
- immintrin/_mm256_castpd128_pd256
- immintrin/_mm256_castpd256_pd128
- immintrin/_mm256_castps_pd
- immintrin/_mm256_castps_si256
- immintrin/_mm256_castps128_ps256
- immintrin/_mm256_castps256_ps128
- immintrin/_mm256_castsi128_si256
- immintrin/_mm256_castsi256_pd
- immintrin/_mm256_castsi256_ps
- immintrin/_mm256_castsi256_si128
- ammintrin/_mm256_cmov_si256
- immintrin/_mm256_cmp_pd
- immintrin/_mm256_cmp_ps
- immintrin/_mm256_cmpeq_epi16
- immintrin/_mm256_cmpeq_epi32
- immintrin/_mm256_cmpeq_epi64
- immintrin/_mm256_cmpeq_epi8
- immintrin/_mm256_cmpgt_epi16
- immintrin/_mm256_cmpgt_epi32
- immintrin/_mm256_cmpgt_epi64
- immintrin/_mm256_cmpgt_epi8
- immintrin/_mm256_cvtepi16_epi32
- immintrin/_mm256_cvtepi16_epi64
- immintrin/_mm256_cvtepi32_epi64
- immintrin/_mm256_cvtepi32_pd
- immintrin/_mm256_cvtepi32_ps
- immintrin/_mm256_cvtepi8_epi16
- immintrin/_mm256_cvtepi8_epi32
- immintrin/_mm256_cvtepi8_epi64
- immintrin/_mm256_cvtepu16_epi32
- immintrin/_mm256_cvtepu16_epi64
- immintrin/_mm256_cvtepu32_epi64
- immintrin/_mm256_cvtepu8_epi16
- immintrin/_mm256_cvtepu8_epi32
- immintrin/_mm256_cvtepu8_epi64
- immintrin/_mm256_cvtpd_epi32
- immintrin/_mm256_cvtpd_ps
- immintrin/_mm256_cvtph_ps
- immintrin/_mm256_cvtps_epi32
- immintrin/_mm256_cvtps_pd
- immintrin/_mm256_cvtps_ph
- immintrin/_mm256_cvttpd_epi32
- immintrin/_mm256_cvttps_epi32
- immintrin/_mm256_div_pd
- immintrin/_mm256_div_ps
- immintrin/_mm256_dp_ps
- immintrin/_mm256_extractf128_pd
- immintrin/_mm256_extractf128_ps
- immintrin/_mm256_extractf128_si256
- immintrin/_mm256_extracti128_si256
- immintrin/_mm256_fmadd_pd
- immintrin/_mm256_fmadd_ps
- immintrin/_mm256_fmaddsub_pd
- immintrin/_mm256_fmaddsub_ps
- immintrin/_mm256_fmsub_pd
- immintrin/_mm256_fmsub_ps
- immintrin/_mm256_fmsubadd_pd
- immintrin/_mm256_fmsubadd_ps
- immintrin/_mm256_fnmadd_pd
- immintrin/_mm256_fnmadd_ps
- immintrin/_mm256_fnmsub_pd
- immintrin/_mm256_fnmsub_ps
- ammintrin/_mm256_frcz_pd
- ammintrin/_mm256_frcz_ps
- immintrin/_mm256_hadd_epi16
- immintrin/_mm256_hadd_epi32
- immintrin/_mm256_hadd_pd
- immintrin/_mm256_hadd_ps
- immintrin/_mm256_hadds_epi16
- immintrin/_mm256_hsub_epi16
- immintrin/_mm256_hsub_epi32
- immintrin/_mm256_hsub_pd
- immintrin/_mm256_hsub_ps
- immintrin/_mm256_hsubs_epi16
- immintrin/_mm256_i32gather_epi32
- immintrin/_mm256_i32gather_epi64
- immintrin/_mm256_i32gather_pd
- immintrin/_mm256_i32gather_ps
- immintrin/_mm256_i64gather_epi32
- immintrin/_mm256_i64gather_epi64
- immintrin/_mm256_i64gather_pd
- immintrin/_mm256_i64gather_ps
- immintrin/_mm256_insertf128_pd
- immintrin/_mm256_insertf128_ps
- immintrin/_mm256_insertf128_si256
- immintrin/_mm256_inserti128_si256
- immintrin/_mm256_lddqu_si256
- immintrin/_mm256_load_pd
- immintrin/_mm256_load_ps
- immintrin/_mm256_load_si256
- immintrin/_mm256_loadu_pd
- immintrin/_mm256_loadu_ps
- immintrin/_mm256_loadu_si256
- ammintrin/_mm256_macc_pd
- ammintrin/_mm256_macc_ps
- immintrin/_mm256_madd_epi16
- ammintrin/_mm256_maddsub_pd
- ammintrin/_mm256_maddsub_ps
- immintrin/_mm256_maddubs_epi16
- immintrin/_mm256_mask_i32gather_epi32
- immintrin/_mm256_mask_i32gather_epi64
- immintrin/_mm256_mask_i32gather_pd
- immintrin/_mm256_mask_i32gather_ps
- immintrin/_mm256_mask_i64gather_epi32
- immintrin/_mm256_mask_i64gather_epi64
- immintrin/_mm256_mask_i64gather_pd
- immintrin/_mm256_mask_i64gather_ps
- immintrin/_mm256_maskload_epi32
- immintrin/_mm256_maskload_epi64
- immintrin/_mm256_maskload_pd
- immintrin/_mm256_maskload_ps
- immintrin/_mm256_maskstore_epi32
- immintrin/_mm256_maskstore_epi64
- immintrin/_mm256_maskstore_pd
- immintrin/_mm256_maskstore_ps
- immintrin/_mm256_max_epi16
- immintrin/_mm256_max_epi32
- immintrin/_mm256_max_epi8
- immintrin/_mm256_max_epu16
- immintrin/_mm256_max_epu32
- immintrin/_mm256_max_epu8
- immintrin/_mm256_max_pd
- immintrin/_mm256_max_ps
- immintrin/_mm256_min_epi16
- immintrin/_mm256_min_epi32
- immintrin/_mm256_min_epi8
- immintrin/_mm256_min_epu16
- immintrin/_mm256_min_epu32
- immintrin/_mm256_min_epu8
- immintrin/_mm256_min_pd
- immintrin/_mm256_min_ps
- immintrin/_mm256_movedup_pd
- immintrin/_mm256_movehdup_ps
- immintrin/_mm256_moveldup_ps
- immintrin/_mm256_movemask_epi8
- immintrin/_mm256_movemask_pd
- immintrin/_mm256_movemask_ps
- immintrin/_mm256_mpsadbw_epu8
- ammintrin/_mm256_msub_pd
- ammintrin/_mm256_msub_ps
- ammintrin/_mm256_msubadd_pd
- ammintrin/_mm256_msubadd_ps
- immintrin/_mm256_mul_epi32
- immintrin/_mm256_mul_epu32
- immintrin/_mm256_mul_pd
- immintrin/_mm256_mul_ps
- immintrin/_mm256_mulhi_epi16
- immintrin/_mm256_mulhi_epu16
- immintrin/_mm256_mulhrs_epi16
- immintrin/_mm256_mullo_epi16
- immintrin/_mm256_mullo_epi32
- ammintrin/_mm256_nmacc_pd
- ammintrin/_mm256_nmacc_ps
- ammintrin/_mm256_nmsub_pd
- ammintrin/_mm256_nmsub_ps
- immintrin/_mm256_or_pd
- immintrin/_mm256_or_ps
- immintrin/_mm256_or_si256
- immintrin/_mm256_packs_epi16
- immintrin/_mm256_packs_epi32
- immintrin/_mm256_packus_epi16
- immintrin/_mm256_packus_epi32
- immintrin/_mm256_permute_pd
- immintrin/_mm256_permute_ps
- ammintrin/_mm256_permute2_pd
- ammintrin/_mm256_permute2_ps
- immintrin/_mm256_permute2f128_pd
- immintrin/_mm256_permute2f128_ps
- immintrin/_mm256_permute2f128_si256
- immintrin/_mm256_permute2x128_si256
- immintrin/_mm256_permute4x64_epi64
- immintrin/_mm256_permute4x64_pd
- immintrin/_mm256_permutevar_pd
- immintrin/_mm256_permutevar_ps
- immintrin/_mm256_permutevar8x32_epi32
- immintrin/_mm256_permutevar8x32_ps
- immintrin/_mm256_rcp_ps
- immintrin/_mm256_round_pd
- immintrin/_mm256_round_ps
- immintrin/_mm256_rsqrt_ps
- immintrin/_mm256_sad_epu8
- immintrin/_mm256_set_epi16
- immintrin/_mm256_set_epi32
- immintrin/_mm256_set_epi8
- immintrin/_mm256_set_pd
- immintrin/_mm256_set_ps
- immintrin/_mm256_set1_epi16
- immintrin/_mm256_set1_epi32
- immintrin/_mm256_set1_epi8
- immintrin/_mm256_set1_pd
- immintrin/_mm256_set1_ps
- immintrin/_mm256_setr_epi16
- immintrin/_mm256_setr_epi32
- immintrin/_mm256_setr_epi8
- immintrin/_mm256_setr_pd
- immintrin/_mm256_setr_ps
- immintrin/_mm256_setzero_pd
- immintrin/_mm256_setzero_ps
- immintrin/_mm256_setzero_si256
- immintrin/_mm256_shuffle_epi32
- immintrin/_mm256_shuffle_epi8
- immintrin/_mm256_shuffle_pd
- immintrin/_mm256_shuffle_ps
- immintrin/_mm256_shufflehi_epi16
- immintrin/_mm256_shufflelo_epi16
- immintrin/_mm256_sign_epi16
- immintrin/_mm256_sign_epi32
- immintrin/_mm256_sign_epi8
- immintrin/_mm256_sll_epi16
- immintrin/_mm256_sll_epi32
- immintrin/_mm256_sll_epi64
- immintrin/_mm256_slli_epi16
- immintrin/_mm256_slli_epi32
- immintrin/_mm256_slli_epi64
- immintrin/_mm256_slli_si256
- immintrin/_mm256_sllv_epi32
- immintrin/_mm256_sllv_epi64
- immintrin/_mm256_sqrt_pd
- immintrin/_mm256_sqrt_ps
- immintrin/_mm256_sra_epi16
- immintrin/_mm256_sra_epi32
- immintrin/_mm256_srai_epi16
- immintrin/_mm256_srai_epi32
- immintrin/_mm256_srav_epi32
- immintrin/_mm256_srl_epi16
- immintrin/_mm256_srl_epi32
- immintrin/_mm256_srl_epi64
- immintrin/_mm256_srli_epi16
- immintrin/_mm256_srli_epi32
- immintrin/_mm256_srli_epi64
- immintrin/_mm256_srli_si256
- immintrin/_mm256_srlv_epi32
- immintrin/_mm256_srlv_epi64
- immintrin/_mm256_store_pd
- immintrin/_mm256_store_ps
- immintrin/_mm256_store_si256
- immintrin/_mm256_storeu_pd
- immintrin/_mm256_storeu_ps
- immintrin/_mm256_storeu_si256
- immintrin/_mm256_stream_load_si256
- immintrin/_mm256_stream_pd
- immintrin/_mm256_stream_ps
- immintrin/_mm256_stream_si256
- immintrin/_mm256_sub_epi16
- immintrin/_mm256_sub_epi32
- immintrin/_mm256_sub_epi64
- immintrin/_mm256_sub_epi8
- immintrin/_mm256_sub_pd
- immintrin/_mm256_sub_ps
- immintrin/_mm256_subs_epi16
- immintrin/_mm256_subs_epi8
- immintrin/_mm256_subs_epu16
- immintrin/_mm256_subs_epu8
- immintrin/_mm256_testc_pd
- immintrin/_mm256_testc_ps
- immintrin/_mm256_testc_si256
- immintrin/_mm256_testnzc_pd
- immintrin/_mm256_testnzc_ps
- immintrin/_mm256_testnzc_si256
- immintrin/_mm256_testz_pd
- immintrin/_mm256_testz_ps
- immintrin/_mm256_testz_si256
- immintrin/_mm256_unpackhi_epi16
- immintrin/_mm256_unpackhi_epi32
- immintrin/_mm256_unpackhi_epi64
- immintrin/_mm256_unpackhi_epi8
- immintrin/_mm256_unpackhi_pd
- immintrin/_mm256_unpackhi_ps
- immintrin/_mm256_unpacklo_epi16
- immintrin/_mm256_unpacklo_epi32
- immintrin/_mm256_unpacklo_epi64
- immintrin/_mm256_unpacklo_epi8
- immintrin/_mm256_unpacklo_pd
- immintrin/_mm256_unpacklo_ps
- immintrin/_mm256_xor_pd
- immintrin/_mm256_xor_ps
- immintrin/_mm256_xor_si256
- immintrin/_mm256_zeroall
- immintrin/_mm256_zeroupper
- immintrin/_mulx_u32
- intrin/__nvreg_restore_fence
- intrin/__nvreg_save_fence
- immintrin/_pdep_u32
- immintrin/_pext_u32
- immintrin/_rdrand16_step
- immintrin/_rdrand32_step
- immintrin/_rdseed16_step
- immintrin/_rdseed32_step
- immintrin/_rorx_u32
- intrin/_rsm
- immintrin/_sarx_i32
- intrin/_sgdt
- immintrin/_shlx_u32
- immintrin/_shrx_u32
- ammintrin/__slwpcb
- intrin/_stac
- immintrin/_store_be_u16
- immintrin/_storebe_i16
- immintrin/_store_be_u32
- immintrin/_storebe_i32
- immintrin/_Store_HLERelease
- immintrin/_StorePointer_HLERelease
- intrin/_subborrow_u16
- intrin/_subborrow_u32
- intrin/_subborrow_u8
- ammintrin/_t1mskc_u32
- ammintrin/_tzcnt_u32
- ammintrin/_tzmsk_u32
- immintrin/_xabort
- immintrin/_xbegin
- immintrin/_xend
- immintrin/_xgetbv
- immintrin/_xrstor
- immintrin/_xsave
- immintrin/_xsaveopt
- immintrin/_xsetbv
- immintrin/_xtest
helpviewer_keywords:
- cl.exe compiler, intrinsics
- intrinsics, x86
- _addcarry_u16 x86 intrinsic
- _addcarry_u32 x86 intrinsic
- _addcarry_u8 x86 intrinsic
- _addcarryx_u32 x86 intrinsic
- _andn_u32 x86 intrinsic
- _bextr_u32 x86 intrinsic
- _bextri_u32 x86 intrinsic
- _blcfill_u32 x86 intrinsic
- _blci_u32 x86 intrinsic
- _blcic_u32 x86 intrinsic
- _blcmsk_u32 x86 intrinsic
- _blcs_u32 x86 intrinsic
- _blsfill_u32 x86 intrinsic
- _blsi_u32 x86 intrinsic
- _blsic_u32 x86 intrinsic
- _blsmsk_u32 x86 intrinsic
- _blsr_u32 x86 intrinsic
- _bzhi_u32 x86 intrinsic
- _clac x86 intrinsic
- _fxrstor x86 intrinsic
- _fxsave x86 intrinsic
- _invpcid x86 intrinsic
- _lgdt x86 intrinsic
- _load_be_u16 x86 intrinsic
- _loadbe_i16 x86 intrinsic
- _load_be_u32 x86 intrinsic
- _loadbe_i32 x86 intrinsic
- __llwpcb x86 intrinsic
- __lwpins32 x86 intrinsic
- __lwpval32 x86 intrinsic
- _lzcnt_u32 x86 intrinsic
- _m_empty x86 intrinsic
- _m_femms x86 intrinsic
- _m_from_float x86 intrinsic
- _m_from_int x86 intrinsic
- _m_maskmovq x86 intrinsic
- _m_packssdw x86 intrinsic
- _m_packsswb x86 intrinsic
- _m_packuswb x86 intrinsic
- _m_paddb x86 intrinsic
- _m_paddd x86 intrinsic
- _m_paddsb x86 intrinsic
- _m_paddsw x86 intrinsic
- _m_paddusb x86 intrinsic
- _m_paddusw x86 intrinsic
- _m_paddw x86 intrinsic
- _m_pand x86 intrinsic
- _m_pandn x86 intrinsic
- _m_pavgb x86 intrinsic
- _m_pavgusb x86 intrinsic
- _m_pavgw x86 intrinsic
- _m_pcmpeqb x86 intrinsic
- _m_pcmpeqd x86 intrinsic
- _m_pcmpeqw x86 intrinsic
- _m_pcmpgtb x86 intrinsic
- _m_pcmpgtd x86 intrinsic
- _m_pcmpgtw x86 intrinsic
- _m_pextrw x86 intrinsic
- _m_pf2id x86 intrinsic
- _m_pf2iw x86 intrinsic
- _m_pfacc x86 intrinsic
- _m_pfadd x86 intrinsic
- _m_pfcmpeq x86 intrinsic
- _m_pfcmpge x86 intrinsic
- _m_pfcmpgt x86 intrinsic
- _m_pfmax x86 intrinsic
- _m_pfmin x86 intrinsic
- _m_pfmul x86 intrinsic
- _m_pfnacc x86 intrinsic
- _m_pfpnacc x86 intrinsic
- _m_pfrcp x86 intrinsic
- _m_pfrcpit1 x86 intrinsic
- _m_pfrcpit2 x86 intrinsic
- _m_pfrsqit1 x86 intrinsic
- _m_pfrsqrt x86 intrinsic
- _m_pfsub x86 intrinsic
- _m_pfsubr x86 intrinsic
- _m_pi2fd x86 intrinsic
- _m_pi2fw x86 intrinsic
- _m_pinsrw x86 intrinsic
- _m_pmaddwd x86 intrinsic
- _m_pmaxsw x86 intrinsic
- _m_pmaxub x86 intrinsic
- _m_pminsw x86 intrinsic
- _m_pminub x86 intrinsic
- _m_pmovmskb x86 intrinsic
- _m_pmulhrw x86 intrinsic
- _m_pmulhuw x86 intrinsic
- _m_pmulhw x86 intrinsic
- _m_pmullw x86 intrinsic
- _m_por x86 intrinsic
- _m_prefetch x86 intrinsic
- _m_prefetchw x86 intrinsic
- _m_psadbw x86 intrinsic
- _m_pshufw x86 intrinsic
- _m_pslld x86 intrinsic
- _m_pslldi x86 intrinsic
- _m_psllq x86 intrinsic
- _m_psllqi x86 intrinsic
- _m_psllw x86 intrinsic
- _m_psllwi x86 intrinsic
- _m_psrad x86 intrinsic
- _m_psradi x86 intrinsic
- _m_psraw x86 intrinsic
- _m_psrawi x86 intrinsic
- _m_psrld x86 intrinsic
- _m_psrldi x86 intrinsic
- _m_psrlq x86 intrinsic
- _m_psrlqi x86 intrinsic
- _m_psrlw x86 intrinsic
- _m_psrlwi x86 intrinsic
- _m_psubb x86 intrinsic
- _m_psubd x86 intrinsic
- _m_psubsb x86 intrinsic
- _m_psubsw x86 intrinsic
- _m_psubusb x86 intrinsic
- _m_psubusw x86 intrinsic
- _m_psubw x86 intrinsic
- _m_pswapd x86 intrinsic
- _m_punpckhbw x86 intrinsic
- _m_punpckhdq x86 intrinsic
- _m_punpckhwd x86 intrinsic
- _m_punpcklbw x86 intrinsic
- _m_punpckldq x86 intrinsic
- _m_punpcklwd x86 intrinsic
- _m_pxor x86 intrinsic
- _m_to_float x86 intrinsic
- _m_to_int x86 intrinsic
- _mm_abs_epi16 x86 intrinsic
- _mm_abs_epi32 x86 intrinsic
- _mm_abs_epi8 x86 intrinsic
- _mm_abs_pi16 x86 intrinsic
- _mm_abs_pi32 x86 intrinsic
- _mm_abs_pi8 x86 intrinsic
- _mm_add_epi16 x86 intrinsic
- _mm_add_epi32 x86 intrinsic
- _mm_add_epi64 x86 intrinsic
- _mm_add_epi8 x86 intrinsic
- _mm_add_pd x86 intrinsic
- _mm_add_pi8 x86 intrinsic
- _mm_add_pi16 x86 intrinsic
- _mm_add_pi32 x86 intrinsic
- _mm_add_ps x86 intrinsic
- _mm_add_sd x86 intrinsic
- _mm_add_si64 x86 intrinsic
- _mm_add_ss x86 intrinsic
- _mm_adds_epi16 x86 intrinsic
- _mm_adds_epi8 x86 intrinsic
- _mm_adds_epu16 x86 intrinsic
- _mm_adds_epu8 x86 intrinsic
- _mm_adds_pi8 x86 intrinsic
- _mm_adds_pi16 x86 intrinsic
- _mm_adds_pu8 x86 intrinsic
- _mm_adds_pu16 x86 intrinsic
- _mm_addsub_pd x86 intrinsic
- _mm_addsub_ps x86 intrinsic
- _mm_aesdec_si128 x86 intrinsic
- _mm_aesdeclast_si128 x86 intrinsic
- _mm_aesenc_si128 x86 intrinsic
- _mm_aesenclast_si128 x86 intrinsic
- _mm_aesimc_si128 x86 intrinsic
- _mm_aeskeygenassist_si128 x86 intrinsic
- _mm_alignr_epi8 x86 intrinsic
- _mm_alignr_pi8 x86 intrinsic
- _mm_and_pd x86 intrinsic
- _mm_and_ps x86 intrinsic
- _mm_and_si64 x86 intrinsic
- _mm_and_si128 x86 intrinsic
- _mm_andnot_pd x86 intrinsic
- _mm_andnot_ps x86 intrinsic
- _mm_andnot_si64 x86 intrinsic
- _mm_andnot_si128 x86 intrinsic
- _mm_avg_epu16 x86 intrinsic
- _mm_avg_epu8 x86 intrinsic
- _mm_blend_epi16 x86 intrinsic
- _mm_blend_epi32 x86 intrinsic
- _mm_blend_pd x86 intrinsic
- _mm_blend_ps x86 intrinsic
- _mm_blendv_epi8 x86 intrinsic
- _mm_blendv_pd x86 intrinsic
- _mm_blendv_ps x86 intrinsic
- _mm_broadcast_ss x86 intrinsic
- _mm_broadcastb_epi8 x86 intrinsic
- _mm_broadcastd_epi32 x86 intrinsic
- _mm_broadcastq_epi64 x86 intrinsic
- _mm_broadcastsd_pd x86 intrinsic
- _mm_broadcastss_ps x86 intrinsic
- _mm_broadcastw_epi16 x86 intrinsic
- _mm_castpd_ps x86 intrinsic
- _mm_castpd_si128 x86 intrinsic
- _mm_castps_pd x86 intrinsic
- _mm_castps_si128 x86 intrinsic
- _mm_castsi128_pd x86 intrinsic
- _mm_castsi128_ps x86 intrinsic
- _mm_clflush x86 intrinsic
- _mm_clmulepi64_si128 x86 intrinsic
- _mm_cmov_si128 x86 intrinsic
- _mm_cmp_pd x86 intrinsic
- _mm_cmp_ps x86 intrinsic
- _mm_cmp_sd x86 intrinsic
- _mm_cmp_ss x86 intrinsic
- _mm_cmpeq_epi16 x86 intrinsic
- _mm_cmpeq_epi32 x86 intrinsic
- _mm_cmpeq_epi64 x86 intrinsic
- _mm_cmpeq_epi8 x86 intrinsic
- _mm_cmpeq_pd x86 intrinsic
- _mm_cmpeq_pi8 x86 intrinsic
- _mm_cmpeq_pi16 x86 intrinsic
- _mm_cmpeq_pi32 x86 intrinsic
- _mm_cmpeq_ps x86 intrinsic
- _mm_cmpeq_sd x86 intrinsic
- _mm_cmpeq_ss x86 intrinsic
- _mm_cmpestra x86 intrinsic
- _mm_cmpestrc x86 intrinsic
- _mm_cmpestri x86 intrinsic
- _mm_cmpestrm x86 intrinsic
- _mm_cmpestro x86 intrinsic
- _mm_cmpestrs x86 intrinsic
- _mm_cmpestrz x86 intrinsic
- _mm_cmpge_pd x86 intrinsic
- _mm_cmpge_ps x86 intrinsic
- _mm_cmpge_sd x86 intrinsic
- _mm_cmpge_ss x86 intrinsic
- _mm_cmpgt_epi16 x86 intrinsic
- _mm_cmpgt_epi32 x86 intrinsic
- _mm_cmpgt_epi64 x86 intrinsic
- _mm_cmpgt_epi8 x86 intrinsic
- _mm_cmpgt_pi8 x86 intrinsic
- _mm_cmpgt_pi16 x86 intrinsic
- _mm_cmpgt_pi32 x86 intrinsic
- _mm_cmpgt_pd x86 intrinsic
- _mm_cmpgt_ps x86 intrinsic
- _mm_cmpgt_sd x86 intrinsic
- _mm_cmpgt_ss x86 intrinsic
- _mm_cmpistra x86 intrinsic
- _mm_cmpistrc x86 intrinsic
- _mm_cmpistri x86 intrinsic
- _mm_cmpistrm x86 intrinsic
- _mm_cmpistro x86 intrinsic
- _mm_cmpistrs x86 intrinsic
- _mm_cmpistrz x86 intrinsic
- _mm_cmple_pd x86 intrinsic
- _mm_cmple_ps x86 intrinsic
- _mm_cmple_sd x86 intrinsic
- _mm_cmple_ss x86 intrinsic
- _mm_cmplt_epi16 x86 intrinsic
- _mm_cmplt_epi32 x86 intrinsic
- _mm_cmplt_epi8 x86 intrinsic
- _mm_cmplt_pd x86 intrinsic
- _mm_cmplt_ps x86 intrinsic
- _mm_cmplt_sd x86 intrinsic
- _mm_cmplt_ss x86 intrinsic
- _mm_cmpneq_pd x86 intrinsic
- _mm_cmpneq_ps x86 intrinsic
- _mm_cmpneq_sd x86 intrinsic
- _mm_cmpneq_ss x86 intrinsic
- _mm_cmpnge_pd x86 intrinsic
- _mm_cmpnge_ps x86 intrinsic
- _mm_cmpnge_sd x86 intrinsic
- _mm_cmpnge_ss x86 intrinsic
- _mm_cmpngt_pd x86 intrinsic
- _mm_cmpngt_ps x86 intrinsic
- _mm_cmpngt_sd x86 intrinsic
- _mm_cmpngt_ss x86 intrinsic
- _mm_cmpnle_pd x86 intrinsic
- _mm_cmpnle_ps x86 intrinsic
- _mm_cmpnle_sd x86 intrinsic
- _mm_cmpnle_ss x86 intrinsic
- _mm_cmpnlt_pd x86 intrinsic
- _mm_cmpnlt_ps x86 intrinsic
- _mm_cmpnlt_sd x86 intrinsic
- _mm_cmpnlt_ss x86 intrinsic
- _mm_cmpord_pd x86 intrinsic
- _mm_cmpord_ps x86 intrinsic
- _mm_cmpord_sd x86 intrinsic
- _mm_cmpord_ss x86 intrinsic
- _mm_cmpunord_pd x86 intrinsic
- _mm_cmpunord_ps x86 intrinsic
- _mm_cmpunord_sd x86 intrinsic
- _mm_cmpunord_ss x86 intrinsic
- _mm_com_epi16 x86 intrinsic
- _mm_com_epi32 x86 intrinsic
- _mm_com_epi64 x86 intrinsic
- _mm_com_epi8 x86 intrinsic
- _mm_com_epu16 x86 intrinsic
- _mm_com_epu32 x86 intrinsic
- _mm_com_epu64 x86 intrinsic
- _mm_com_epu8 x86 intrinsic
- _mm_comieq_sd x86 intrinsic
- _mm_comieq_ss x86 intrinsic
- _mm_comige_sd x86 intrinsic
- _mm_comige_ss x86 intrinsic
- _mm_comigt_sd x86 intrinsic
- _mm_comigt_ss x86 intrinsic
- _mm_comile_sd x86 intrinsic
- _mm_comile_ss x86 intrinsic
- _mm_comilt_sd x86 intrinsic
- _mm_comilt_ss x86 intrinsic
- _mm_comineq_sd x86 intrinsic
- _mm_comineq_ss x86 intrinsic
- _mm_crc32_u16 x86 intrinsic
- _mm_crc32_u32 x86 intrinsic
- _mm_crc32_u8 x86 intrinsic
- _mm_cvt_pi2ps x86 intrinsic
- _mm_cvt_ps2pi x86 intrinsic
- _mm_cvt_si2ss x86 intrinsic
- _mm_cvt_ss2si x86 intrinsic
- _mm_cvtepi16_epi32 x86 intrinsic
- _mm_cvtepi16_epi64 x86 intrinsic
- _mm_cvtepi32_epi64 x86 intrinsic
- _mm_cvtepi32_pd x86 intrinsic
- _mm_cvtepi32_ps x86 intrinsic
- _mm_cvtepi8_epi16 x86 intrinsic
- _mm_cvtepi8_epi32 x86 intrinsic
- _mm_cvtepi8_epi64 x86 intrinsic
- _mm_cvtepu16_epi32 x86 intrinsic
- _mm_cvtepu16_epi64 x86 intrinsic
- _mm_cvtepu32_epi64 x86 intrinsic
- _mm_cvtepu8_epi16 x86 intrinsic
- _mm_cvtepu8_epi32 x86 intrinsic
- _mm_cvtepu8_epi64 x86 intrinsic
- _mm_cvtpd_epi32 x86 intrinsic
- _mm_cvtpd_pi32 x86 intrinsic
- _mm_cvtpd_ps x86 intrinsic
- _mm_cvtph_ps x86 intrinsic
- _mm_cvtpi32_pd x86 intrinsic
- _mm_cvtps_epi32 x86 intrinsic
- _mm_cvtps_pd x86 intrinsic
- _mm_cvtps_ph x86 intrinsic
- _mm_cvtsd_f64 x86 intrinsic
- _mm_cvtsd_si32 x86 intrinsic
- _mm_cvtsd_ss x86 intrinsic
- _mm_cvtsi128_si32 x86 intrinsic
- _mm_cvtsi32_sd x86 intrinsic
- _mm_cvtsi32_si128 x86 intrinsic
- _mm_cvtsi32_si64 x86 intrinsic
- _mm_cvtsi64_si32 x86 intrinsic
- _mm_cvtss_f32 x86 intrinsic
- _mm_cvtss_sd x86 intrinsic
- _mm_cvtt_ps2pi x86 intrinsic
- _mm_cvtt_ss2si x86 intrinsic
- _mm_cvttpd_epi32 x86 intrinsic
- _mm_cvttpd_pi32 x86 intrinsic
- _mm_cvttps_epi32 x86 intrinsic
- _mm_cvttsd_si32 x86 intrinsic
- _mm_div_pd x86 intrinsic
- _mm_div_ps x86 intrinsic
- _mm_div_sd x86 intrinsic
- _mm_div_ss x86 intrinsic
- _mm_dp_pd x86 intrinsic
- _mm_dp_ps x86 intrinsic
- _mm_empty x86 intrinsic
- _mm_extract_epi16 x86 intrinsic
- _mm_extract_epi32 x86 intrinsic
- _mm_extract_epi8 x86 intrinsic
- _mm_extract_ps x86 intrinsic
- _mm_fmadd_pd x86 intrinsic
- _mm_fmadd_ps x86 intrinsic
- _mm_fmadd_sd x86 intrinsic
- _mm_fmadd_ss x86 intrinsic
- _mm_fmaddsub_pd x86 intrinsic
- _mm_fmaddsub_ps x86 intrinsic
- _mm_fmsub_pd x86 intrinsic
- _mm_fmsub_ps x86 intrinsic
- _mm_fmsub_sd x86 intrinsic
- _mm_fmsub_ss x86 intrinsic
- _mm_fmsubadd_pd x86 intrinsic
- _mm_fmsubadd_ps x86 intrinsic
- _mm_fnmadd_pd x86 intrinsic
- _mm_fnmadd_ps x86 intrinsic
- _mm_fnmadd_sd x86 intrinsic
- _mm_fnmadd_ss x86 intrinsic
- _mm_fnmsub_pd x86 intrinsic
- _mm_fnmsub_ps x86 intrinsic
- _mm_fnmsub_sd x86 intrinsic
- _mm_fnmsub_ss x86 intrinsic
- _mm_frcz_pd x86 intrinsic
- _mm_frcz_ps x86 intrinsic
- _mm_frcz_sd x86 intrinsic
- _mm_frcz_ss x86 intrinsic
- _mm_getcsr x86 intrinsic
- _mm_hadd_epi16 x86 intrinsic
- _mm_hadd_epi32 x86 intrinsic
- _mm_hadd_pd x86 intrinsic
- _mm_hadd_pi16 x86 intrinsic
- _mm_hadd_pi32 x86 intrinsic
- _mm_hadd_ps x86 intrinsic
- _mm_haddd_epi16 x86 intrinsic
- _mm_haddd_epi8 x86 intrinsic
- _mm_haddd_epu16 x86 intrinsic
- _mm_haddd_epu8 x86 intrinsic
- _mm_haddq_epi16 x86 intrinsic
- _mm_haddq_epi32 x86 intrinsic
- _mm_haddq_epi8 x86 intrinsic
- _mm_haddq_epu16 x86 intrinsic
- _mm_haddq_epu32 x86 intrinsic
- _mm_haddq_epu8 x86 intrinsic
- _mm_hadds_epi16 x86 intrinsic
- _mm_hadds_pi16 x86 intrinsic
- _mm_haddw_epi8 x86 intrinsic
- _mm_haddw_epu8 x86 intrinsic
- _mm_hsub_epi16 x86 intrinsic
- _mm_hsub_epi32 x86 intrinsic
- _mm_hsub_pd x86 intrinsic
- _mm_hsub_pi16 x86 intrinsic
- _mm_hsub_pi32 x86 intrinsic
- _mm_hsub_ps x86 intrinsic
- _mm_hsubd_epi16 x86 intrinsic
- _mm_hsubq_epi32 x86 intrinsic
- _mm_hsubs_epi16 x86 intrinsic
- _mm_hsubs_pi16 x86 intrinsic
- _mm_hsubw_epi8 x86 intrinsic
- _mm_i32gather_epi32 x86 intrinsic
- _mm_i32gather_epi64 x86 intrinsic
- _mm_i32gather_pd x86 intrinsic
- _mm_i32gather_ps x86 intrinsic
- _mm_i64gather_epi32 x86 intrinsic
- _mm_i64gather_epi64 x86 intrinsic
- _mm_i64gather_pd x86 intrinsic
- _mm_i64gather_ps x86 intrinsic
- _mm_insert_epi16 x86 intrinsic
- _mm_insert_epi32 x86 intrinsic
- _mm_insert_epi8 x86 intrinsic
- _mm_insert_ps x86 intrinsic
- _mm_lddqu_si128 x86 intrinsic
- _mm_lfence x86 intrinsic
- _mm_load_pd x86 intrinsic
- _mm_load_ps x86 intrinsic
- _mm_load_ps1 x86 intrinsic
- _mm_load_sd x86 intrinsic
- _mm_load_si128 x86 intrinsic
- _mm_load_ss x86 intrinsic
- _mm_load1_pd x86 intrinsic
- _mm_loaddup_pd x86 intrinsic
- _mm_loadh_pd x86 intrinsic
- _mm_loadh_pi x86 intrinsic
- _mm_loadl_epi64 x86 intrinsic
- _mm_loadl_pd x86 intrinsic
- _mm_loadl_pi x86 intrinsic
- _mm_loadr_pd x86 intrinsic
- _mm_loadr_ps x86 intrinsic
- _mm_loadu_pd x86 intrinsic
- _mm_loadu_ps x86 intrinsic
- _mm_loadu_si128 x86 intrinsic
- _mm_macc_epi16 x86 intrinsic
- _mm_macc_epi32 x86 intrinsic
- _mm_macc_pd x86 intrinsic
- _mm_macc_ps x86 intrinsic
- _mm_macc_sd x86 intrinsic
- _mm_macc_ss x86 intrinsic
- _mm_maccd_epi16 x86 intrinsic
- _mm_macchi_epi32 x86 intrinsic
- _mm_macclo_epi32 x86 intrinsic
- _mm_maccs_epi16 x86 intrinsic
- _mm_maccs_epi32 x86 intrinsic
- _mm_maccsd_epi16 x86 intrinsic
- _mm_maccshi_epi32 x86 intrinsic
- _mm_maccslo_epi32 x86 intrinsic
- _mm_madd_epi16 x86 intrinsic
- _mm_madd_pi16 x86 intrinsic
- _mm_maddd_epi16 x86 intrinsic
- _mm_maddsd_epi16 x86 intrinsic
- _mm_maddsub_pd x86 intrinsic
- _mm_maddsub_ps x86 intrinsic
- _mm_maddubs_epi16 x86 intrinsic
- _mm_maddubs_pi16 x86 intrinsic
- _mm_mask_i32gather_epi32 x86 intrinsic
- _mm_mask_i32gather_epi64 x86 intrinsic
- _mm_mask_i32gather_pd x86 intrinsic
- _mm_mask_i32gather_ps x86 intrinsic
- _mm_mask_i64gather_epi32 x86 intrinsic
- _mm_mask_i64gather_epi64 x86 intrinsic
- _mm_mask_i64gather_pd x86 intrinsic
- _mm_mask_i64gather_ps x86 intrinsic
- _mm_maskload_epi32 x86 intrinsic
- _mm_maskload_epi64 x86 intrinsic
- _mm_maskload_pd x86 intrinsic
- _mm_maskload_ps x86 intrinsic
- _mm_maskmoveu_si128 x86 intrinsic
- _mm_maskstore_epi32 x86 intrinsic
- _mm_maskstore_epi64 x86 intrinsic
- _mm_maskstore_pd x86 intrinsic
- _mm_maskstore_ps x86 intrinsic
- _mm_max_epi16 x86 intrinsic
- _mm_max_epi32 x86 intrinsic
- _mm_max_epi8 x86 intrinsic
- _mm_max_epu16 x86 intrinsic
- _mm_max_epu32 x86 intrinsic
- _mm_max_epu8 x86 intrinsic
- _mm_max_pd x86 intrinsic
- _mm_max_ps x86 intrinsic
- _mm_max_sd x86 intrinsic
- _mm_max_ss x86 intrinsic
- _mm_mfence x86 intrinsic
- _mm_min_epi16 x86 intrinsic
- _mm_min_epi32 x86 intrinsic
- _mm_min_epi8 x86 intrinsic
- _mm_min_epu16 x86 intrinsic
- _mm_min_epu32 x86 intrinsic
- _mm_min_epu8 x86 intrinsic
- _mm_min_pd x86 intrinsic
- _mm_min_ps x86 intrinsic
- _mm_min_sd x86 intrinsic
- _mm_min_ss x86 intrinsic
- _mm_minpos_epu16 x86 intrinsic
- _mm_monitor x86 intrinsic
- _mm_move_epi64 x86 intrinsic
- _mm_move_sd x86 intrinsic
- _mm_move_ss x86 intrinsic
- _mm_movedup_pd x86 intrinsic
- _mm_movehdup_ps x86 intrinsic
- _mm_movehl_ps x86 intrinsic
- _mm_moveldup_ps x86 intrinsic
- _mm_movelh_ps x86 intrinsic
- _mm_movemask_epi8 x86 intrinsic
- _mm_movemask_pd x86 intrinsic
- _mm_movemask_ps x86 intrinsic
- _mm_movepi64_pi64 x86 intrinsic
- _mm_movpi64_epi64 x86 intrinsic
- _mm_mpsadbw_epu8 x86 intrinsic
- _mm_msub_pd x86 intrinsic
- _mm_msub_ps x86 intrinsic
- _mm_msub_sd x86 intrinsic
- _mm_msub_ss x86 intrinsic
- _mm_msubadd_pd x86 intrinsic
- _mm_msubadd_ps x86 intrinsic
- _mm_mul_epi32 x86 intrinsic
- _mm_mul_epu32 x86 intrinsic
- _mm_mul_pd x86 intrinsic
- _mm_mul_ps x86 intrinsic
- _mm_mul_sd x86 intrinsic
- _mm_mul_ss x86 intrinsic
- _mm_mul_su32 x86 intrinsic
- _mm_mulhi_epi16 x86 intrinsic
- _mm_mulhi_epu16 x86 intrinsic
- _mm_mulhi_pi16 x86 intrinsic
- _mm_mulhrs_epi16 x86 intrinsic
- _mm_mulhrs_pi16 x86 intrinsic
- _mm_mullo_epi16 x86 intrinsic
- _mm_mullo_epi32 x86 intrinsic
- _mm_mullo_pi16 x86 intrinsic
- _mm_mwait x86 intrinsic
- _mm_nmacc_pd x86 intrinsic
- _mm_nmacc_ps x86 intrinsic
- _mm_nmacc_sd x86 intrinsic
- _mm_nmacc_ss x86 intrinsic
- _mm_nmsub_pd x86 intrinsic
- _mm_nmsub_ps x86 intrinsic
- _mm_nmsub_sd x86 intrinsic
- _mm_nmsub_ss x86 intrinsic
- _mm_or_pd x86 intrinsic
- _mm_or_ps x86 intrinsic
- _mm_or_si64 x86 intrinsic
- _mm_or_si128 x86 intrinsic
- _mm_packs_epi16 x86 intrinsic
- _mm_packs_epi32 x86 intrinsic
- _mm_packs_pi16 x86 intrinsic
- _mm_packs_pi32 x86 intrinsic
- _mm_packs_pu16 x86 intrinsic
- _mm_packus_epi16 x86 intrinsic
- _mm_packus_epi32 x86 intrinsic
- _mm_pause x86 intrinsic
- _mm_perm_epi8 x86 intrinsic
- _mm_permute_pd x86 intrinsic
- _mm_permute_ps x86 intrinsic
- _mm_permute2_pd x86 intrinsic
- _mm_permute2_ps x86 intrinsic
- _mm_permutevar_pd x86 intrinsic
- _mm_permutevar_ps x86 intrinsic
- _mm_popcnt_u32 x86 intrinsic
- _mm_prefetch x86 intrinsic
- _mm_rcp_ps x86 intrinsic
- _mm_rcp_ss x86 intrinsic
- _mm_rot_epi16 x86 intrinsic
- _mm_rot_epi32 x86 intrinsic
- _mm_rot_epi64 x86 intrinsic
- _mm_rot_epi8 x86 intrinsic
- _mm_roti_epi16 x86 intrinsic
- _mm_roti_epi32 x86 intrinsic
- _mm_roti_epi64 x86 intrinsic
- _mm_roti_epi8 x86 intrinsic
- _mm_round_pd x86 intrinsic
- _mm_round_ps x86 intrinsic
- _mm_round_sd x86 intrinsic
- _mm_round_ss x86 intrinsic
- _mm_rsqrt_ps x86 intrinsic
- _mm_rsqrt_ss x86 intrinsic
- _mm_sad_epu8 x86 intrinsic
- _mm_set_epi16 x86 intrinsic
- _mm_set_epi32 x86 intrinsic
- _mm_set_epi64 x86 intrinsic
- _mm_set_epi8 x86 intrinsic
- _mm_set_pd x86 intrinsic
- _mm_set_pi16 x86 intrinsic
- _mm_set_pi32 x86 intrinsic
- _mm_set_pi8 x86 intrinsic
- _mm_set_ps x86 intrinsic
- _mm_set_ps1 x86 intrinsic
- _mm_set_sd x86 intrinsic
- _mm_set_ss x86 intrinsic
- _mm_set1_epi16 x86 intrinsic
- _mm_set1_epi32 x86 intrinsic
- _mm_set1_epi64 x86 intrinsic
- _mm_set1_epi8 x86 intrinsic
- _mm_set1_pd x86 intrinsic
- _mm_set1_pi16 x86 intrinsic
- _mm_set1_pi32 x86 intrinsic
- _mm_set1_pi8 x86 intrinsic
- _mm_setcsr x86 intrinsic
- _mm_setl_epi64 x86 intrinsic
- _mm_setr_epi16 x86 intrinsic
- _mm_setr_epi32 x86 intrinsic
- _mm_setr_epi64 x86 intrinsic
- _mm_setr_epi8 x86 intrinsic
- _mm_setr_pd x86 intrinsic
- _mm_setr_pi16 x86 intrinsic
- _mm_setr_pi32 x86 intrinsic
- _mm_setr_pi8 x86 intrinsic
- _mm_setr_ps x86 intrinsic
- _mm_setzero_pd x86 intrinsic
- _mm_setzero_ps x86 intrinsic
- _mm_setzero_si128 x86 intrinsic
- _mm_setzero_si64 x86 intrinsic
- _mm_sfence x86 intrinsic
- _mm_sha_epi16 x86 intrinsic
- _mm_sha_epi32 x86 intrinsic
- _mm_sha_epi64 x86 intrinsic
- _mm_sha_epi8 x86 intrinsic
- _mm_shl_epi16 x86 intrinsic
- _mm_shl_epi32 x86 intrinsic
- _mm_shl_epi64 x86 intrinsic
- _mm_shl_epi8 x86 intrinsic
- _mm_shuffle_epi32 x86 intrinsic
- _mm_shuffle_epi8 x86 intrinsic
- _mm_shuffle_pd x86 intrinsic
- _mm_shuffle_pi8 x86 intrinsic
- _mm_shuffle_ps x86 intrinsic
- _mm_shufflehi_epi16 x86 intrinsic
- _mm_shufflelo_epi16 x86 intrinsic
- _mm_sign_epi16 x86 intrinsic
- _mm_sign_epi32 x86 intrinsic
- _mm_sign_epi8 x86 intrinsic
- _mm_sign_pi16 x86 intrinsic
- _mm_sign_pi32 x86 intrinsic
- _mm_sign_pi8 x86 intrinsic
- _mm_sll_epi16 x86 intrinsic
- _mm_sll_epi32 x86 intrinsic
- _mm_sll_epi64 x86 intrinsic
- _mm_sll_pi16 x86 intrinsic
- _mm_sll_pi32 x86 intrinsic
- _mm_sll_si64 x86 intrinsic
- _mm_slli_epi16 x86 intrinsic
- _mm_slli_epi32 x86 intrinsic
- _mm_slli_epi64 x86 intrinsic
- _mm_slli_pi16 x86 intrinsic
- _mm_slli_pi32 x86 intrinsic
- _mm_slli_si64 x86 intrinsic
- _mm_slli_si128 x86 intrinsic
- _mm_sllv_epi32 x86 intrinsic
- _mm_sllv_epi64 x86 intrinsic
- _mm_sqrt_pd x86 intrinsic
- _mm_sqrt_ps x86 intrinsic
- _mm_sqrt_sd x86 intrinsic
- _mm_sqrt_ss x86 intrinsic
- _mm_sra_epi16 x86 intrinsic
- _mm_sra_epi32 x86 intrinsic
- _mm_sra_pi16 x86 intrinsic
- _mm_sra_pi32 x86 intrinsic
- _mm_srai_epi16 x86 intrinsic
- _mm_srai_epi32 x86 intrinsic
- _mm_srai_pi16 x86 intrinsic
- _mm_srai_pi32 x86 intrinsic
- _mm_srav_epi32 x86 intrinsic
- _mm_srl_epi16 x86 intrinsic
- _mm_srl_epi32 x86 intrinsic
- _mm_srl_epi64 x86 intrinsic
- _mm_srl_pi16 x86 intrinsic
- _mm_srl_pi32 x86 intrinsic
- _mm_srl_si64 x86 intrinsic
- _mm_srli_epi16 x86 intrinsic
- _mm_srli_epi32 x86 intrinsic
- _mm_srli_epi64 x86 intrinsic
- _mm_srli_pi16 x86 intrinsic
- _mm_srli_pi32 x86 intrinsic
- _mm_srli_si64 x86 intrinsic
- _mm_srli_si128 x86 intrinsic
- _mm_srlv_epi32 x86 intrinsic
- _mm_srlv_epi64 x86 intrinsic
- _mm_store_pd x86 intrinsic
- _mm_store_ps x86 intrinsic
- _mm_store_ps1 x86 intrinsic
- _mm_store_sd x86 intrinsic
- _mm_store_si128 x86 intrinsic
- _mm_store_ss x86 intrinsic
- _mm_store1_pd x86 intrinsic
- _mm_storeh_pd x86 intrinsic
- _mm_storeh_pi x86 intrinsic
- _mm_storel_epi64 x86 intrinsic
- _mm_storel_pd x86 intrinsic
- _mm_storel_pi x86 intrinsic
- _mm_storer_pd x86 intrinsic
- _mm_storer_ps x86 intrinsic
- _mm_storeu_pd x86 intrinsic
- _mm_storeu_ps x86 intrinsic
- _mm_storeu_si128 x86 intrinsic
- _mm_stream_load_si128 x86 intrinsic
- _mm_stream_pd x86 intrinsic
- _mm_stream_pi x86 intrinsic
- _mm_stream_ps x86 intrinsic
- _mm_stream_si128 x86 intrinsic
- _mm_stream_si32 x86 intrinsic
- _mm_sub_epi16 x86 intrinsic
- _mm_sub_epi32 x86 intrinsic
- _mm_sub_epi64 x86 intrinsic
- _mm_sub_epi8 x86 intrinsic
- _mm_sub_pd x86 intrinsic
- _mm_sub_pi8 x86 intrinsic
- _mm_sub_pi16 x86 intrinsic
- _mm_sub_pi32 x86 intrinsic
- _mm_sub_ps x86 intrinsic
- _mm_sub_sd x86 intrinsic
- _mm_sub_si64 x86 intrinsic
- _mm_sub_ss x86 intrinsic
- _mm_subs_epi16 x86 intrinsic
- _mm_subs_epi8 x86 intrinsic
- _mm_subs_epu16 x86 intrinsic
- _mm_subs_epu8 x86 intrinsic
- _mm_subs_pi8 x86 intrinsic
- _mm_subs_pi16 x86 intrinsic
- _mm_subs_pu8 x86 intrinsic
- _mm_subs_pu16 x86 intrinsic
- _mm_testc_pd x86 intrinsic
- _mm_testc_ps x86 intrinsic
- _mm_testc_si128 x86 intrinsic
- _mm_testnzc_pd x86 intrinsic
- _mm_testnzc_ps x86 intrinsic
- _mm_testnzc_si128 x86 intrinsic
- _mm_testz_pd x86 intrinsic
- _mm_testz_ps x86 intrinsic
- _mm_testz_si128 x86 intrinsic
- _mm_ucomieq_sd x86 intrinsic
- _mm_ucomieq_ss x86 intrinsic
- _mm_ucomige_sd x86 intrinsic
- _mm_ucomige_ss x86 intrinsic
- _mm_ucomigt_sd x86 intrinsic
- _mm_ucomigt_ss x86 intrinsic
- _mm_ucomile_sd x86 intrinsic
- _mm_ucomile_ss x86 intrinsic
- _mm_ucomilt_sd x86 intrinsic
- _mm_ucomilt_ss x86 intrinsic
- _mm_ucomineq_sd x86 intrinsic
- _mm_ucomineq_ss x86 intrinsic
- _mm_unpackhi_epi16 x86 intrinsic
- _mm_unpackhi_epi32 x86 intrinsic
- _mm_unpackhi_epi64 x86 intrinsic
- _mm_unpackhi_epi8 x86 intrinsic
- _mm_unpackhi_pd x86 intrinsic
- _mm_unpackhi_pi8 x86 intrinsic
- _mm_unpackhi_pi16 x86 intrinsic
- _mm_unpackhi_pi32 x86 intrinsic
- _mm_unpackhi_ps x86 intrinsic
- _mm_unpacklo_epi16 x86 intrinsic
- _mm_unpacklo_epi32 x86 intrinsic
- _mm_unpacklo_epi64 x86 intrinsic
- _mm_unpacklo_epi8 x86 intrinsic
- _mm_unpacklo_pd x86 intrinsic
- _mm_unpacklo_pi8 x86 intrinsic
- _mm_unpacklo_pi16 x86 intrinsic
- _mm_unpacklo_pi32 x86 intrinsic
- _mm_unpacklo_ps x86 intrinsic
- _mm_xor_pd x86 intrinsic
- _mm_xor_ps x86 intrinsic
- _mm_xor_si64 x86 intrinsic
- _mm_xor_si128 x86 intrinsic
- _mm256_abs_epi16 x86 intrinsic
- _mm256_abs_epi32 x86 intrinsic
- _mm256_abs_epi8 x86 intrinsic
- _mm256_add_epi16 x86 intrinsic
- _mm256_add_epi32 x86 intrinsic
- _mm256_add_epi64 x86 intrinsic
- _mm256_add_epi8 x86 intrinsic
- _mm256_add_pd x86 intrinsic
- _mm256_add_ps x86 intrinsic
- _mm256_adds_epi16 x86 intrinsic
- _mm256_adds_epi8 x86 intrinsic
- _mm256_adds_epu16 x86 intrinsic
- _mm256_adds_epu8 x86 intrinsic
- _mm256_addsub_pd x86 intrinsic
- _mm256_addsub_ps x86 intrinsic
- _mm256_alignr_epi8 x86 intrinsic
- _mm256_and_pd x86 intrinsic
- _mm256_and_ps x86 intrinsic
- _mm256_and_si256 x86 intrinsic
- _mm256_andnot_pd x86 intrinsic
- _mm256_andnot_ps x86 intrinsic
- _mm256_andnot_si256 x86 intrinsic
- _mm256_avg_epu16 x86 intrinsic
- _mm256_avg_epu8 x86 intrinsic
- _mm256_blend_epi16 x86 intrinsic
- _mm256_blend_epi32 x86 intrinsic
- _mm256_blend_pd x86 intrinsic
- _mm256_blend_ps x86 intrinsic
- _mm256_blendv_epi8 x86 intrinsic
- _mm256_blendv_pd x86 intrinsic
- _mm256_blendv_ps x86 intrinsic
- _mm256_broadcast_pd x86 intrinsic
- _mm256_broadcast_ps x86 intrinsic
- _mm256_broadcast_sd x86 intrinsic
- _mm256_broadcast_ss x86 intrinsic
- _mm256_broadcastb_epi8 x86 intrinsic
- _mm256_broadcastd_epi32 x86 intrinsic
- _mm256_broadcastq_epi64 x86 intrinsic
- _mm256_broadcastsd_pd x86 intrinsic
- _mm256_broadcastsi128_si256 x86 intrinsic
- _mm256_broadcastss_ps x86 intrinsic
- _mm256_broadcastw_epi16 x86 intrinsic
- _mm256_castpd_ps x86 intrinsic
- _mm256_castpd_si256 x86 intrinsic
- _mm256_castpd128_pd256 x86 intrinsic
- _mm256_castpd256_pd128 x86 intrinsic
- _mm256_castps_pd x86 intrinsic
- _mm256_castps_si256 x86 intrinsic
- _mm256_castps128_ps256 x86 intrinsic
- _mm256_castps256_ps128 x86 intrinsic
- _mm256_castsi128_si256 x86 intrinsic
- _mm256_castsi256_pd x86 intrinsic
- _mm256_castsi256_ps x86 intrinsic
- _mm256_castsi256_si128 x86 intrinsic
- _mm256_cmov_si256 x86 intrinsic
- _mm256_cmp_pd x86 intrinsic
- _mm256_cmp_ps x86 intrinsic
- _mm256_cmpeq_epi16 x86 intrinsic
- _mm256_cmpeq_epi32 x86 intrinsic
- _mm256_cmpeq_epi64 x86 intrinsic
- _mm256_cmpeq_epi8 x86 intrinsic
- _mm256_cmpgt_epi16 x86 intrinsic
- _mm256_cmpgt_epi32 x86 intrinsic
- _mm256_cmpgt_epi64 x86 intrinsic
- _mm256_cmpgt_epi8 x86 intrinsic
- _mm256_cvtepi16_epi32 x86 intrinsic
- _mm256_cvtepi16_epi64 x86 intrinsic
- _mm256_cvtepi32_epi64 x86 intrinsic
- _mm256_cvtepi32_pd x86 intrinsic
- _mm256_cvtepi32_ps x86 intrinsic
- _mm256_cvtepi8_epi16 x86 intrinsic
- _mm256_cvtepi8_epi32 x86 intrinsic
- _mm256_cvtepi8_epi64 x86 intrinsic
- _mm256_cvtepu16_epi32 x86 intrinsic
- _mm256_cvtepu16_epi64 x86 intrinsic
- _mm256_cvtepu32_epi64 x86 intrinsic
- _mm256_cvtepu8_epi16 x86 intrinsic
- _mm256_cvtepu8_epi32 x86 intrinsic
- _mm256_cvtepu8_epi64 x86 intrinsic
- _mm256_cvtpd_epi32 x86 intrinsic
- _mm256_cvtpd_ps x86 intrinsic
- _mm256_cvtph_ps x86 intrinsic
- _mm256_cvtps_epi32 x86 intrinsic
- _mm256_cvtps_pd x86 intrinsic
- _mm256_cvtps_ph x86 intrinsic
- _mm256_cvttpd_epi32 x86 intrinsic
- _mm256_cvttps_epi32 x86 intrinsic
- _mm256_div_pd x86 intrinsic
- _mm256_div_ps x86 intrinsic
- _mm256_dp_ps x86 intrinsic
- _mm256_extractf128_pd x86 intrinsic
- _mm256_extractf128_ps x86 intrinsic
- _mm256_extractf128_si256 x86 intrinsic
- _mm256_extracti128_si256 x86 intrinsic
- _mm256_fmadd_pd x86 intrinsic
- _mm256_fmadd_ps x86 intrinsic
- _mm256_fmaddsub_pd x86 intrinsic
- _mm256_fmaddsub_ps x86 intrinsic
- _mm256_fmsub_pd x86 intrinsic
- _mm256_fmsub_ps x86 intrinsic
- _mm256_fmsubadd_pd x86 intrinsic
- _mm256_fmsubadd_ps x86 intrinsic
- _mm256_fnmadd_pd x86 intrinsic
- _mm256_fnmadd_ps x86 intrinsic
- _mm256_fnmsub_pd x86 intrinsic
- _mm256_fnmsub_ps x86 intrinsic
- _mm256_frcz_pd x86 intrinsic
- _mm256_frcz_ps x86 intrinsic
- _mm256_hadd_epi16 x86 intrinsic
- _mm256_hadd_epi32 x86 intrinsic
- _mm256_hadd_pd x86 intrinsic
- _mm256_hadd_ps x86 intrinsic
- _mm256_hadds_epi16 x86 intrinsic
- _mm256_hsub_epi16 x86 intrinsic
- _mm256_hsub_epi32 x86 intrinsic
- _mm256_hsub_pd x86 intrinsic
- _mm256_hsub_ps x86 intrinsic
- _mm256_hsubs_epi16 x86 intrinsic
- _mm256_i32gather_epi32 x86 intrinsic
- _mm256_i32gather_epi64 x86 intrinsic
- _mm256_i32gather_pd x86 intrinsic
- _mm256_i32gather_ps x86 intrinsic
- _mm256_i64gather_epi32 x86 intrinsic
- _mm256_i64gather_epi64 x86 intrinsic
- _mm256_i64gather_pd x86 intrinsic
- _mm256_i64gather_ps x86 intrinsic
- _mm256_insertf128_pd x86 intrinsic
- _mm256_insertf128_ps x86 intrinsic
- _mm256_insertf128_si256 x86 intrinsic
- _mm256_inserti128_si256 x86 intrinsic
- _mm256_lddqu_si256 x86 intrinsic
- _mm256_load_pd x86 intrinsic
- _mm256_load_ps x86 intrinsic
- _mm256_load_si256 x86 intrinsic
- _mm256_loadu_pd x86 intrinsic
- _mm256_loadu_ps x86 intrinsic
- _mm256_loadu_si256 x86 intrinsic
- _mm256_macc_pd x86 intrinsic
- _mm256_macc_ps x86 intrinsic
- _mm256_madd_epi16 x86 intrinsic
- _mm256_maddsub_pd x86 intrinsic
- _mm256_maddsub_ps x86 intrinsic
- _mm256_maddubs_epi16 x86 intrinsic
- _mm256_mask_i32gather_epi32 x86 intrinsic
- _mm256_mask_i32gather_epi64 x86 intrinsic
- _mm256_mask_i32gather_pd x86 intrinsic
- _mm256_mask_i32gather_ps x86 intrinsic
- _mm256_mask_i64gather_epi32 x86 intrinsic
- _mm256_mask_i64gather_epi64 x86 intrinsic
- _mm256_mask_i64gather_pd x86 intrinsic
- _mm256_mask_i64gather_ps x86 intrinsic
- _mm256_maskload_epi32 x86 intrinsic
- _mm256_maskload_epi64 x86 intrinsic
- _mm256_maskload_pd x86 intrinsic
- _mm256_maskload_ps x86 intrinsic
- _mm256_maskstore_epi32 x86 intrinsic
- _mm256_maskstore_epi64 x86 intrinsic
- _mm256_maskstore_pd x86 intrinsic
- _mm256_maskstore_ps x86 intrinsic
- _mm256_max_epi16 x86 intrinsic
- _mm256_max_epi32 x86 intrinsic
- _mm256_max_epi8 x86 intrinsic
- _mm256_max_epu16 x86 intrinsic
- _mm256_max_epu32 x86 intrinsic
- _mm256_max_epu8 x86 intrinsic
- _mm256_max_pd x86 intrinsic
- _mm256_max_ps x86 intrinsic
- _mm256_min_epi16 x86 intrinsic
- _mm256_min_epi32 x86 intrinsic
- _mm256_min_epi8 x86 intrinsic
- _mm256_min_epu16 x86 intrinsic
- _mm256_min_epu32 x86 intrinsic
- _mm256_min_epu8 x86 intrinsic
- _mm256_min_pd x86 intrinsic
- _mm256_min_ps x86 intrinsic
- _mm256_movedup_pd x86 intrinsic
- _mm256_movehdup_ps x86 intrinsic
- _mm256_moveldup_ps x86 intrinsic
- _mm256_movemask_epi8 x86 intrinsic
- _mm256_movemask_pd x86 intrinsic
- _mm256_movemask_ps x86 intrinsic
- _mm256_mpsadbw_epu8 x86 intrinsic
- _mm256_msub_pd x86 intrinsic
- _mm256_msub_ps x86 intrinsic
- _mm256_msubadd_pd x86 intrinsic
- _mm256_msubadd_ps x86 intrinsic
- _mm256_mul_epi32 x86 intrinsic
- _mm256_mul_epu32 x86 intrinsic
- _mm256_mul_pd x86 intrinsic
- _mm256_mul_ps x86 intrinsic
- _mm256_mulhi_epi16 x86 intrinsic
- _mm256_mulhi_epu16 x86 intrinsic
- _mm256_mulhrs_epi16 x86 intrinsic
- _mm256_mullo_epi16 x86 intrinsic
- _mm256_mullo_epi32 x86 intrinsic
- _mm256_nmacc_pd x86 intrinsic
- _mm256_nmacc_ps x86 intrinsic
- _mm256_nmsub_pd x86 intrinsic
- _mm256_nmsub_ps x86 intrinsic
- _mm256_or_pd x86 intrinsic
- _mm256_or_ps x86 intrinsic
- _mm256_or_si256 x86 intrinsic
- _mm256_packs_epi16 x86 intrinsic
- _mm256_packs_epi32 x86 intrinsic
- _mm256_packus_epi16 x86 intrinsic
- _mm256_packus_epi32 x86 intrinsic
- _mm256_permute_pd x86 intrinsic
- _mm256_permute_ps x86 intrinsic
- _mm256_permute2_pd x86 intrinsic
- _mm256_permute2_ps x86 intrinsic
- _mm256_permute2f128_pd x86 intrinsic
- _mm256_permute2f128_ps x86 intrinsic
- _mm256_permute2f128_si256 x86 intrinsic
- _mm256_permute2x128_si256 x86 intrinsic
- _mm256_permute4x64_epi64 x86 intrinsic
- _mm256_permute4x64_pd x86 intrinsic
- _mm256_permutevar_pd x86 intrinsic
- _mm256_permutevar_ps x86 intrinsic
- _mm256_permutevar8x32_epi32 x86 intrinsic
- _mm256_permutevar8x32_ps x86 intrinsic
- _mm256_rcp_ps x86 intrinsic
- _mm256_round_pd x86 intrinsic
- _mm256_round_ps x86 intrinsic
- _mm256_rsqrt_ps x86 intrinsic
- _mm256_sad_epu8 x86 intrinsic
- _mm256_set_epi16 x86 intrinsic
- _mm256_set_epi32 x86 intrinsic
- _mm256_set_epi8 x86 intrinsic
- _mm256_set_pd x86 intrinsic
- _mm256_set_ps x86 intrinsic
- _mm256_set1_epi16 x86 intrinsic
- _mm256_set1_epi32 x86 intrinsic
- _mm256_set1_epi8 x86 intrinsic
- _mm256_set1_pd x86 intrinsic
- _mm256_set1_ps x86 intrinsic
- _mm256_setr_epi16 x86 intrinsic
- _mm256_setr_epi32 x86 intrinsic
- _mm256_setr_epi8 x86 intrinsic
- _mm256_setr_pd x86 intrinsic
- _mm256_setr_ps x86 intrinsic
- _mm256_setzero_pd x86 intrinsic
- _mm256_setzero_ps x86 intrinsic
- _mm256_setzero_si256 x86 intrinsic
- _mm256_shuffle_epi32 x86 intrinsic
- _mm256_shuffle_epi8 x86 intrinsic
- _mm256_shuffle_pd x86 intrinsic
- _mm256_shuffle_ps x86 intrinsic
- _mm256_shufflehi_epi16 x86 intrinsic
- _mm256_shufflelo_epi16 x86 intrinsic
- _mm256_sign_epi16 x86 intrinsic
- _mm256_sign_epi32 x86 intrinsic
- _mm256_sign_epi8 x86 intrinsic
- _mm256_sll_epi16 x86 intrinsic
- _mm256_sll_epi32 x86 intrinsic
- _mm256_sll_epi64 x86 intrinsic
- _mm256_slli_epi16 x86 intrinsic
- _mm256_slli_epi32 x86 intrinsic
- _mm256_slli_epi64 x86 intrinsic
- _mm256_slli_si256 x86 intrinsic
- _mm256_sllv_epi32 x86 intrinsic
- _mm256_sllv_epi64 x86 intrinsic
- _mm256_sqrt_pd x86 intrinsic
- _mm256_sqrt_ps x86 intrinsic
- _mm256_sra_epi16 x86 intrinsic
- _mm256_sra_epi32 x86 intrinsic
- _mm256_srai_epi16 x86 intrinsic
- _mm256_srai_epi32 x86 intrinsic
- _mm256_srav_epi32 x86 intrinsic
- _mm256_srl_epi16 x86 intrinsic
- _mm256_srl_epi32 x86 intrinsic
- _mm256_srl_epi64 x86 intrinsic
- _mm256_srli_epi16 x86 intrinsic
- _mm256_srli_epi32 x86 intrinsic
- _mm256_srli_epi64 x86 intrinsic
- _mm256_srli_si256 x86 intrinsic
- _mm256_srlv_epi32 x86 intrinsic
- _mm256_srlv_epi64 x86 intrinsic
- _mm256_store_pd x86 intrinsic
- _mm256_store_ps x86 intrinsic
- _mm256_store_si256 x86 intrinsic
- _mm256_storeu_pd x86 intrinsic
- _mm256_storeu_ps x86 intrinsic
- _mm256_storeu_si256 x86 intrinsic
- _mm256_stream_load_si256 x86 intrinsic
- _mm256_stream_pd x86 intrinsic
- _mm256_stream_ps x86 intrinsic
- _mm256_stream_si256 x86 intrinsic
- _mm256_sub_epi16 x86 intrinsic
- _mm256_sub_epi32 x86 intrinsic
- _mm256_sub_epi64 x86 intrinsic
- _mm256_sub_epi8 x86 intrinsic
- _mm256_sub_pd x86 intrinsic
- _mm256_sub_ps x86 intrinsic
- _mm256_subs_epi16 x86 intrinsic
- _mm256_subs_epi8 x86 intrinsic
- _mm256_subs_epu16 x86 intrinsic
- _mm256_subs_epu8 x86 intrinsic
- _mm256_testc_pd x86 intrinsic
- _mm256_testc_ps x86 intrinsic
- _mm256_testc_si256 x86 intrinsic
- _mm256_testnzc_pd x86 intrinsic
- _mm256_testnzc_ps x86 intrinsic
- _mm256_testnzc_si256 x86 intrinsic
- _mm256_testz_pd x86 intrinsic
- _mm256_testz_ps x86 intrinsic
- _mm256_testz_si256 x86 intrinsic
- _mm256_unpackhi_epi16 x86 intrinsic
- _mm256_unpackhi_epi32 x86 intrinsic
- _mm256_unpackhi_epi64 x86 intrinsic
- _mm256_unpackhi_epi8 x86 intrinsic
- _mm256_unpackhi_pd x86 intrinsic
- _mm256_unpackhi_ps x86 intrinsic
- _mm256_unpacklo_epi16 x86 intrinsic
- _mm256_unpacklo_epi32 x86 intrinsic
- _mm256_unpacklo_epi64 x86 intrinsic
- _mm256_unpacklo_epi8 x86 intrinsic
- _mm256_unpacklo_pd x86 intrinsic
- _mm256_unpacklo_ps x86 intrinsic
- _mm256_xor_pd x86 intrinsic
- _mm256_xor_ps x86 intrinsic
- _mm256_xor_si256 x86 intrinsic
- _mm256_zeroall x86 intrinsic
- _mm256_zeroupper x86 intrinsic
- _mulx_u32 x86 intrinsic
- __nvreg_restore_fence x86 intrinsic
- __nvreg_save_fence x86 intrinsic
- _pdep_u32 x86 intrinsic
- _pext_u32 x86 intrinsic
- _rdrand16_step x86 intrinsic
- _rdrand32_step x86 intrinsic
- _rdseed16_step x86 intrinsic
- _rdseed32_step x86 intrinsic
- _rorx_u32 x86 intrinsic
- _rsm x86 intrinsic
- _sarx_i32 x86 intrinsic
- _sgdt x86 intrinsic
- _shlx_u32 x86 intrinsic
- _shrx_u32 x86 intrinsic
- __slwpcb x86 intrinsic
- _stac x86 intrinsic
- _store_be_u16 x86 intrinsic
- _storebe_i16 x86 intrinsic
- _store_be_u32 x86 intrinsic
- _storebe_i32 x86 intrinsic
- _Store_HLERelease x86 intrinsic
- _StorePointer_HLERelease x86 intrinsic
- _subborrow_u16 x86 intrinsic
- _subborrow_u32 x86 intrinsic
- _subborrow_u8 x86 intrinsic
- _t1mskc_u32 x86 intrinsic
- _tzcnt_u32 x86 intrinsic
- _tzmsk_u32 x86 intrinsic
- _xabort x86 intrinsic
- _xbegin x86 intrinsic
- _xend x86 intrinsic
- _xgetbv x86 intrinsic
- _xrstor x86 intrinsic
- _xsave x86 intrinsic
- _xsaveopt x86 intrinsic
- _xsetbv x86 intrinsic
- _xtest x86 intrinsic
ms.openlocfilehash: fabc622552003dad3b26d6dfc4e184f1627ce50b
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754296"
---
# <a name="x86-intrinsics-list"></a>x86 內建函式清單

本文檔列出了 Microsoft C/C++ 編譯器在以 x86 為目標時支援的內在內容。

如需個別內建的詳細資訊，請參閱下列適合您的目標處理器的資源：

- 標頭檔。 許多內建函式會記錄在標頭檔中的註解裡。

- [Intel 內建功能指南](https://software.intel.com/sites/landingpage/IntrinsicsGuide/)： 使用搜尋方塊來尋找特定的內建函式。

- [Intel 64 和 IA-32 架構軟體開發人員手冊](https://software.intel.com/articles/intel-sdm)

- [Intel 架構指令集延伸程式設計參考](https://software.intel.com/isa-extensions)

- [英特爾高級向量擴展簡介](https://software.intel.com/articles/introduction-to-intel-advanced-vector-extensions)

- [AMD 開發人員指南、手冊& ISA 文檔](https://developer.amd.com/resources/developer-guides-manuals/)

## <a name="x86-intrinsics"></a>x86 內固

下表列出 x86 處理器上可用的內建。 技術資料行列出必要的指令集支援。 請使用 [__cpuid](cpuid-cpuidex.md) 內建函式在執行階段判斷指令集支援。 如果一個資料列中有兩個項目，則代表同一個內建函式的不同進入點。 [1] 表示內建函式僅可用於 AMD 處理器。 [2] 表示內建函式僅可用於 Intel 處理器。 [3] 表示原型是巨集。 函式原型所需的標頭會列在標頭資料行中。 為了簡化起見，Intrin.h 標頭包含 immintrin.h 和 ammintrin.h。

|內建名稱|技術|頁首|函式原型|
|--------------------|----------------|------------|------------------------|
|_addcarry_u16||intrin.h|無符號字元_addcarry_u16(無符號字元,無符號短,無符號短,無符號短\*)|
|[_addcarry_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_addcarry_u32)||intrin.h|無符號字元_addcarry_u32(無符號字元、無符號 int、無符號 int、無\*符號 int)|
|_addcarry_u8||intrin.h|未簽署的字元_addcarry_u8(無符號字元,無符號字元,無符號字元,無符號\*字元)|
|[_addcarryx_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_addcarryx_u32)|ADX [2]|immintrin.h|無符號字元_addcarryx_u32(無符號字元、無符號 int、無符號 int、無\*符號 int)|
|[__addfsbyte](addfsbyte-addfsword-addfsdword.md)||intrin.h|無效__addfsbyte(無符號長,無符號字元)|
|[__addfsdword](addfsbyte-addfsword-addfsdword.md)||intrin.h|空__addfsdword(無符號長,無符號長)|
|[__addfsword](addfsbyte-addfsword-addfsdword.md)||intrin.h|無效__addfsword(無符號長,無符號短)|
|[_AddressOfReturnAddress](addressofreturnaddress.md)||intrin.h|空\*_AddressOfReturnAddress(空)|
|[_andn_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_andn_u32)|BMI [1]|ammintrin.h|無符號int_andn_u32(無符號int,無符號int)|
|[_bextr_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_bextr_u32)|BMI|ammintrin.h, immintrin.h|無符號 int _bextr_u32(無符號 int,無符號 int,無符號 int)|
|_bextri_u32|ABM [1]|ammintrin.h|無符號int_bextri_u32(無符號int,無符號int)|
|[_BitScanForward](bitscanforward-bitscanforward64.md)||intrin.h|無符號字元_BitScanForward(無符號長\*,無符號長)|
|[_BitScanReverse](bitscanreverse-bitscanreverse64.md)||intrin.h|無符號字元_BitScanReverse(無符號長\*,無符號長)|
|[_bittest](bittest-bittest64.md)||intrin.h|無符號字元_bittest(長孔\*,長)|
|[_bittestandcomplement](bittestandcomplement-bittestandcomplement64.md)||intrin.h|無符號字元_bittestandcomplement(長\*,長)|
|[_bittestandreset](bittestandreset-bittestandreset64.md)||intrin.h|無符號字元_bittestandreset(長\*,長)|
|[_bittestandset](bittestandset-bittestandset64.md)||intrin.h|無符號字元_bittestandset(長\*,長)|
|_blcfill_u32|ABM [1]|ammintrin.h|unsigned int _blcfill_u32(unsigned int)|
|_blci_u32|ABM [1]|ammintrin.h|unsigned int _blci_u32(unsigned int)|
|_blcic_u32|ABM [1]|ammintrin.h|unsigned int _blcic_u32(unsigned int)|
|_blcmsk_u32|ABM [1]|ammintrin.h|unsigned int _blcmsk_u32(unsigned int)|
|_blcs_u32|ABM [1]|ammintrin.h|unsigned int _blcs_u32(unsigned int)|
|_blsfill_u32|ABM [1]|ammintrin.h|unsigned int _blsfill_u32(unsigned int)|
|[_blsi_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_blsi_u32)|BMI|ammintrin.h, immintrin.h|unsigned int _blsi_u32(unsigned int)|
|_blsic_u32|ABM [1]|ammintrin.h|unsigned int _blsic_u32(unsigned int)|
|[_blsmsk_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_blsmsk_u32)|BMI|ammintrin.h, immintrin.h|unsigned int _blsmsk_u32(unsigned int)|
|[_blsr_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_blsr_u32)|BMI|ammintrin.h, immintrin.h|unsigned int _blsr_u32(unsigned int)|
|[_bzhi_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_bzhi_u32)|BMI [2]|immintrin.h|無符號 int _bzhi_u32(無符號 int,無符號 int)|
|_clac|SMAP|intrin.h|void _clac(void)|
|[__cpuid](cpuid-cpuidex.md)||intrin.h|空__cpuid(int, \*int)|
|[__cpuidex](cpuid-cpuidex.md)||intrin.h|空__cpuidex(int, \*int, int)|
|[__debugbreak](debugbreak.md)||intrin.h|void __debugbreak(void)|
|[_disable](disable.md)||intrin.h|void _disable(void)|
|[_div64](div64.md)||intrin.h| int \_div64(_int64,int,int\_ \*)|
|[__emul](emul-emulu.md)||intrin.h|__int64 [帕斯卡/cdecl] \__emul(int, int)|
|[__emulu](emul-emulu.md)||intrin.h|未簽名__int64 [帕斯卡/cdecl]\__emulu(無符號 int,無符號 int)|
|[_enable](enable.md)||intrin.h|void _enable(void)|
|[__fastfail](fastfail.md)||intrin.h|void __fastfail(unsigned int)|
|[_fxrstor](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_fxrstor)|FXSR [2]|immintrin.h|空白_fxrstor(空孔\*)|
|[_fxsave](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_fxsave)|FXSR [2]|immintrin.h|空白_fxsave(空白\*)|
|[__getcallerseflags](getcallerseflags.md)||intrin.h|(unsigned int __getcallerseflags())|
|[__halt](halt.md)||intrin.h|void __halt(void)|
|[__inbyte](inbyte.md)||intrin.h|無符號字元__inbyte(無符號短)|
|[__inbytestring](inbytestring.md)||intrin.h|無效__inbytestring(無符號短,無符號字元\*,無符號長)|
|[__incfsbyte](incfsbyte-incfsword-incfsdword.md)||intrin.h|void __incfsbyte(unsigned long)|
|[__incfsdword](incfsbyte-incfsword-incfsdword.md)||intrin.h|void __incfsdword(unsigned long)|
|[__incfsword](incfsbyte-incfsword-incfsdword.md)||intrin.h|void __incfsword(unsigned long)|
|[__indword](indword.md)||intrin.h|無符號長__indword(無符號短)|
|[__indwordstring](indwordstring.md)||intrin.h|無效__indwordstring(無符號短,無符號長\*,無符號長)|
|[__int2c](int2c.md)||intrin.h|void __int2c(void)|
|[_InterlockedAddLargeStatistic](interlockedaddlargestatistic.md)||intrin.h|長_InterlockedAddLargeStatistic(_int64\_\*揮 發性,長)|
|[_InterlockedAnd](interlockedand-intrinsic-functions.md)||intrin.h|長_InterlockedAnd(長時間揮\*發性,長)|
|[_InterlockedAnd_HLEAcquire](interlockedand-intrinsic-functions.md)|HLE [2]|immintrin.h|長_InterlockedAnd_HLEAcquire(長揮\*發性,長)|
|[_InterlockedAnd_HLERelease](interlockedand-intrinsic-functions.md)|HLE [2]|immintrin.h|長_InterlockedAnd_HLERelease(長時間揮\*發性,長)|
|[_InterlockedAnd16](interlockedand-intrinsic-functions.md)||intrin.h|短_InterlockedAnd16(短波動\*、短)|
|[_InterlockedAnd8](interlockedand-intrinsic-functions.md)||intrin.h|字元_InterlockedAnd8 (字\*元 易揮發 , 字元)|
|[_interlockedbittestandreset](interlockedbittestandreset-intrinsic-functions.md)||intrin.h|無符號字元_interlockedbittestandreset(長\*,長)|
|[_interlockedbittestandreset_HLEAcquire](interlockedbittestandreset-intrinsic-functions.md)|HLE [2]|immintrin.h|無符號字元_interlockedbittestandreset_HLEAcquire(長\*,長)|
|[_interlockedbittestandreset_HLERelease](interlockedbittestandreset-intrinsic-functions.md)|HLE [2]|immintrin.h|無符號字元_interlockedbittestandreset_HLERelease(長\*,長)|
|[_interlockedbittestandset](interlockedbittestandset-intrinsic-functions.md)||intrin.h|無符號字元_interlockedbittestandset(長\*,長)|
|[_interlockedbittestandset_HLEAcquire](interlockedbittestandset-intrinsic-functions.md)|HLE [2]|immintrin.h|無符號字元_interlockedbittestandset_HLEAcquire(長\*,長)|
|[_interlockedbittestandset_HLERelease](interlockedbittestandset-intrinsic-functions.md)|HLE [2]|immintrin.h|無符號字元_interlockedbittestandset_HLERelease(長\*,長)|
|[_InterlockedCompareExchange](interlockedcompareexchange-intrinsic-functions.md)||intrin.h|長_InterlockedCompareExchange(長揮\*發、長、長)|
|[_InterlockedCompareExchange_HLEAcquire](interlockedcompareexchange-intrinsic-functions.md)|HLE [2]|immintrin.h|長_InterlockedCompareExchange_HLEAcquire(長揮\*發、長、長)|
|[_InterlockedCompareExchange_HLERelease](interlockedcompareexchange-intrinsic-functions.md)|HLE [2]|immintrin.h|長_InterlockedCompareExchange_HLERelease(長揮\*發、長、長)|
|[_InterlockedCompareExchange16](interlockedcompareexchange-intrinsic-functions.md)||intrin.h|短_InterlockedCompareExchange16(短波動\*、短、短)|
|[_InterlockedCompareExchange64](interlockedcompareexchange-intrinsic-functions.md)||intrin.h|__int64_InterlockedCompareExchange64(_int64\_波動\*、_int64、_int64) \_ \_|
|[_InterlockedCompareExchange64_HLEAcquire](interlockedcompareexchange-intrinsic-functions.md)|HLE [2]|immintrin.h|__int64_InterlockedCompareExchange64_HLEAcquire(_int64\_\*波動 、_int64、_int64) \_ \_|
|[_InterlockedCompareExchange64_HLERelease](interlockedcompareexchange-intrinsic-functions.md)|HLE [2]|immintrin.h|__int64_InterlockedCompareExchange64_HLERelease(_int64\_\*波動 、_int64、_int64) \_ \_|
|[_InterlockedCompareExchange8](interlockedcompareexchange-intrinsic-functions.md)||intrin.h|字元_InterlockedCompareExchange8 (字\*元 易揮發, 字元, 字元)|
|[_InterlockedCompareExchangePointer](interlockedcompareexchangepointer-intrinsic-functions.md)||intrin.h|空\*_InterlockedCompareExchangePointer(\*空\*揮\*發\*、 空隙、空隙)|
|[_InterlockedCompareExchangePointer_HLEAcquire](interlockedcompareexchangepointer-intrinsic-functions.md)|HLE [2]|immintrin.h|空\*_InterlockedCompareExchangePointer_HLEAcquire(\*空\*揮\*發\*、 空隙、空)|
|[_InterlockedCompareExchangePointer_HLERelease](interlockedcompareexchangepointer-intrinsic-functions.md)|HLE [2]|immintrin.h|空\*_InterlockedCompareExchangePointer_HLERelease(\*空\*揮\*發\*、 空隙、空)|
|[_InterlockedDecrement](interlockeddecrement-intrinsic-functions.md)||intrin.h|長_InterlockedDecrement(長時間揮\*發)|
|[_InterlockedDecrement16](interlockeddecrement-intrinsic-functions.md)||intrin.h|短_InterlockedDecrement16(短揮\*發性)|
|[_InterlockedExchange](interlockedexchange-intrinsic-functions.md)||intrin.h|長_InterlockedExchange(長時間揮\*發性,長)|
|[_InterlockedExchange_HLEAcquire](interlockedexchange-intrinsic-functions.md)|HLE [2]|immintrin.h|長_InterlockedExchange_HLEAcquire(長時間揮\*發性,長)|
|[_InterlockedExchange_HLERelease](interlockedexchange-intrinsic-functions.md)|HLE [2]|immintrin.h|長_InterlockedExchange_HLERelease(長時間揮\*發性,長)|
|[_InterlockedExchange16](interlockedexchange-intrinsic-functions.md)||intrin.h|短_InterlockedExchange16(短波動\*、短)|
|[_InterlockedExchange8](interlockedexchange-intrinsic-functions.md)||intrin.h|字元_InterlockedExchange8 (字\*元 易揮發 , 字元)|
|[_InterlockedExchangeAdd](interlockedexchangeadd-intrinsic-functions.md)||intrin.h|長_InterlockedExchangeAdd(長時間揮\*發性,長)|
|[_InterlockedExchangeAdd_HLEAcquire](interlockedexchangeadd-intrinsic-functions.md)|HLE [2]|immintrin.h|長_InterlockedExchangeAdd_HLEAcquire(長揮\*發性,長)|
|[_InterlockedExchangeAdd_HLERelease](interlockedexchangeadd-intrinsic-functions.md)|HLE [2]|immintrin.h|長_InterlockedExchangeAdd_HLERelease(長時間揮\*發性,長)|
|[_InterlockedExchangeAdd16](interlockedexchangeadd-intrinsic-functions.md)||intrin.h|short _InterlockedExchangeAdd16(short volatile *, short)|
|[_InterlockedExchangeAdd8](interlockedexchangeadd-intrinsic-functions.md)||intrin.h|字元_InterlockedExchangeAdd8 (字\*元 易失性, 字元 )|
|[_InterlockedExchangePointer](interlockedexchangepointer-intrinsic-functions.md)||intrin.h|空\*_InterlockedExchangePointer(\*空\*揮\*發、 空)|
|[_InterlockedExchangePointer_HLEAcquire](interlockedexchangepointer-intrinsic-functions.md)|HLE [2]|immintrin.h|空\*_InterlockedExchangePointer_HLEAcquire(\*空\*揮\*發、 空)|
|[_InterlockedExchangePointer_HLERelease](interlockedexchangepointer-intrinsic-functions.md)|HLE [2]|immintrin.h|空\*_InterlockedExchangePointer_HLERelease(\*\*空\*揮 發性 、 空隙 )|
|[_InterlockedIncrement](interlockedincrement-intrinsic-functions.md)||intrin.h|長_InterlockedIncrement(長時間揮\*發)|
|[_InterlockedIncrement16](interlockedincrement-intrinsic-functions.md)||intrin.h|短_InterlockedIncrement16(短波動\*)|
|[_InterlockedOr](interlockedor-intrinsic-functions.md)||intrin.h|長_InterlockedOr(長時間揮\*發性,長)|
|[_InterlockedOr_HLEAcquire](interlockedor-intrinsic-functions.md)|HLE [2]|immintrin.h|長_InterlockedOr_HLEAcquire(長揮\*發性,長)|
|[_InterlockedOr_HLERelease](interlockedor-intrinsic-functions.md)|HLE [2]|immintrin.h|長_InterlockedOr_HLERelease(長時間揮\*發性,長)|
|[_InterlockedOr16](interlockedor-intrinsic-functions.md)||intrin.h|短_InterlockedOr16(短波動\*、短)|
|[_InterlockedOr8](interlockedor-intrinsic-functions.md)||intrin.h|字元_InterlockedOr8 (字\*元 易揮發 , 字元)|
|[_InterlockedXor](interlockedxor-intrinsic-functions.md)||intrin.h|長_InterlockedXor(長時間揮\*發性,長)|
|[_InterlockedXor_HLEAcquire](interlockedxor-intrinsic-functions.md)|HLE [2]|immintrin.h|長_InterlockedXor_HLEAcquire(長時間揮\*發性,長)|
|[_InterlockedXor_HLERelease](interlockedxor-intrinsic-functions.md)|HLE [2]|immintrin.h|長_InterlockedXor_HLERelease(長時間揮\*發性,長)|
|[_InterlockedXor16](interlockedxor-intrinsic-functions.md)||intrin.h|短_InterlockedXor16(短波動\*、短)|
|[_InterlockedXor8](interlockedxor-intrinsic-functions.md)||intrin.h|字元_InterlockedXor8 (字\*元 易揮發 , 字元)|
|[__invlpg](invlpg.md)||intrin.h|空__invlpg(空\*)|
|[_invpcid](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_invpcid)|INVPCID [2]|immintrin.h|不合法_invpcid(無符號int,\*無效 )|
|[__inword](inword.md)||intrin.h|無符號短__inword(無符號短)|
|[__inwordstring](inwordstring.md)||intrin.h|無效__inwordstring(無符號短,無符號短\*,無符號長)|
|_lgdt||intrin.h|空_lgdt(空\*)|
|[__lidt](lidt.md)||intrin.h|不合法__lidt(\*不合法 )|
|[__ll_lshift](ll-lshift.md)||intrin.h|無符號__int64 [帕斯卡/cdecl] \__ll_lshift(\_未簽名 _int64,int)|
|[__ll_rshift](ll-rshift.md)||intrin.h|__int64 [帕斯\_卡 /cdecl]\__ll_rshift(_int64,int)|
|_load_be_u16<br /><br /> [_loadbe_i16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_loadbe_i16&expand=3071)|MOVBE|immintrin.h|無符號短_load_be_u16(空隙\*);<br /><br /> 短_loadbe_i16(空隙\*);[3]|
|_load_be_u32<br /><br /> [_loadbe_i32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_loadbe_i32&expand=3072)|MOVBE|immintrin.h|無符號_load_be_u32(空錐\*形);<br /><br /> _loadbe_i32(空孔\*);[3]|
|__llwpcb|LWP [1]|ammintrin.h|空白__llwpcb(空\*)|
|__lwpins32|LWP [1]|ammintrin.h|無符號字元__lwpins32(無符號 int,無符號 int,無符號 int)|
|__lwpval32|LWP [1]|ammintrin.h|不合法__lwpval32 (無符號 int、 無符號 int, 無符號 int )|
|[__lzcnt](lzcnt16-lzcnt-lzcnt64.md)|LZCNT|intrin.h|unsigned int __lzcnt(unsigned int)|
|[_lzcnt_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_lzcnt_u32)|BMI|ammintrin.h, immintrin.h|unsigned int _lzcnt_u32(unsigned int)|
|[__lzcnt16](lzcnt16-lzcnt-lzcnt64.md)|LZCNT|intrin.h|unsigned short __lzcnt16(unsigned short)|
|[_m_empty](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_empty)|MMX|intrin.h|void _m_empty(void)|
|_m_femms|3DNOW|intrin.h|void _m_femms(void)|
|_m_from_float|3DNOW|intrin.h|__m64 _m_from_float(float)|
|[_m_from_int](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_from_int)|MMX|intrin.h|__m64 _m_from_int(int)|
|[_m_maskmovq](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_maskmovq)|SSE|intrin.h|空_m_maskmovq(_m64、_m64、\_\_焦\*炭 )|
|[_m_packssdw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_packssdw)|MMX|intrin.h|__m64_m_packssdw(_m64,_m64)\_ \_|
|[_m_packsswb](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_packsswb)|MMX|intrin.h|__m64_m_packsswb(_m64、_m64)\_ \_|
|[_m_packuswb](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_packuswb)|MMX|intrin.h|__m64_m_packuswb(_m64,_m64)\_ \_|
|[_m_paddb](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_paddb)|MMX|intrin.h|__m64_m_paddb(_m64、_m64)\_ \_|
|[_m_paddd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_paddd)|MMX|intrin.h|__m64_m_paddd(_m64、_m64)\_ \_|
|[_m_paddsb](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_paddsb)|MMX|intrin.h|__m64_m_paddsb(_m64、_m64)\_ \_|
|[_m_paddsw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_paddsw)|MMX|intrin.h|__m64_m_paddsw(_m64、_m64)\_ \_|
|[_m_paddusb](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_paddusb)|MMX|intrin.h|__m64_m_paddusb(_m64、_m64)\_ \_|
|[_m_paddusw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_paddusw)|MMX|intrin.h|__m64_m_paddusw(_m64、_m64)\_ \_|
|[_m_paddw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_paddw)|MMX|intrin.h|__m64_m_paddw(_m64、_m64)\_ \_|
|[_m_pand](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pand)|MMX|intrin.h|__m64_m_pand(_m64、_m64)\_ \_|
|[_m_pandn](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pandn)|MMX|intrin.h|__m64_m_pandn(_m64、_m64)\_ \_|
|[_m_pavgb](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pavgb)|SSE|intrin.h|__m64_m_pavgb(_m64、_m64)\_ \_|
|_m_pavgusb|3DNOW|intrin.h|__m64_m_pavgusb(_m64、_m64)\_ \_|
|[_m_pavgw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pavgw)|SSE|intrin.h|__m64_m_pavgw(_m64、_m64)\_ \_|
|[_m_pcmpeqb](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pcmpeqb)|MMX|intrin.h|__m64_m_pcmpeqb(_m64、_m64)\_ \_|
|[_m_pcmpeqd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pcmpeqd)|MMX|intrin.h|__m64_m_pcmpeqd(_m64、_m64)\_ \_|
|[_m_pcmpeqw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pcmpeqw)|MMX|intrin.h|__m64_m_pcmpeqw(_m64、_m64)\_ \_|
|[_m_pcmpgtb](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pcmpgtb)|MMX|intrin.h|__m64_m_pcmpgtb(_m64、_m64)\_ \_|
|[_m_pcmpgtd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pcmpgtd)|MMX|intrin.h|__m64_m_pcmpgtd(_m64、_m64)\_ \_|
|[_m_pcmpgtw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pcmpgtw)|MMX|intrin.h|\___m64_m_pcmpgtw(_m64_m64)\_|
|[_m_pextrw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pextrw)|SSE|intrin.h|_m_pextrw(_m64,int)\_|
|_m_pf2id|3DNOW|intrin.h|__m64_m_pf2id(_m64)\_|
|_m_pf2iw|3DNOWEXT|intrin.h|__m64_m_pf2iw(_m64)\_|
|_m_pfacc|3DNOW|intrin.h|__m64_m_pfacc(_m64、_m64)\_ \_|
|_m_pfadd|3DNOW|intrin.h|__m64_m_pfadd(_m64、_m64)\_ \_|
|_m_pfcmpeq|3DNOW|intrin.h|__m64_m_pfcmpeq(_m64、_m64)\_ \_|
|_m_pfcmpge|3DNOW|intrin.h|__m64_m_pfcmpge(_m64,_m64)\_ \_|
|_m_pfcmpgt|3DNOW|intrin.h|__m64_m_pfcmpgt(_m64、_m64)\_ \_|
|_m_pfmax|3DNOW|intrin.h|__m64_m_pfmax(_m64、_m64)\_ \_|
|_m_pfmin|3DNOW|intrin.h|__m64_m_pfmin(_m64、_m64)\_ \_|
|_m_pfmul|3DNOW|intrin.h|__m64_m_pfmul(_m64、_m64)\_ \_|
|_m_pfnacc|3DNOWEXT|intrin.h|__m64_m_pfnacc(_m64、_m64)\_ \_|
|_m_pfpnacc|3DNOWEXT|intrin.h|__m64_m_pfpnacc(_m64、_m64)\_ \_|
|_m_pfrcp|3DNOW|intrin.h|__m64_m_pfrcp(_m64)\_|
|_m_pfrcpit1|3DNOW|intrin.h|__m64_m_pfrcpit1(_m64,_m64)\_ \_|
|_m_pfrcpit2|3DNOW|intrin.h|__m64_m_pfrcpit2(_m64、_m64)\_ \_|
|_m_pfrsqit1|3DNOW|intrin.h|__m64_m_pfrsqit1(_m64、_m64)\_ \_|
|_m_pfrsqrt|3DNOW|intrin.h|__m64_m_pfrsqrt(_m64)\_|
|_m_pfsub|3DNOW|intrin.h|__m64_m_pfsub(_m64、_m64)\_ \_|
|_m_pfsubr|3DNOW|intrin.h|__m64_m_pfsubr(_m64、_m64)\_ \_|
|_m_pi2fd|3DNOW|intrin.h|__m64_m_pi2fd(_m64)\_|
|_m_pi2fw|3DNOWEXT|intrin.h|__m64_m_pi2fw(_m64)\_|
|[_m_pinsrw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pinsrw)|SSE|intrin.h|__m64_m_pinsrw(_m64、int、int)\_|
|[_m_pmaddwd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pmaddwd)|MMX|intrin.h|__m64_m_pmaddwd(_m64、_m64)\_ \_|
|[_m_pmaxsw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pmaxsw)|SSE|intrin.h|__m64_m_pmaxsw(_m64、_m64)\_ \_|
|[_m_pmaxub](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pmaxub)|SSE|intrin.h|__m64_m_pmaxub(_m64、_m64)\_ \_|
|[_m_pminsw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pminsw)|SSE|intrin.h|__m64_m_pminsw(_m64、_m64)\_ \_|
|[_m_pminub](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pminub)|SSE|intrin.h|__m64_m_pminub(_m64、_m64)\_ \_|
|[_m_pmovmskb](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pmovmskb)|SSE|intrin.h|_m_pmovmskb(_m64)\_|
|_m_pmulhrw|3DNOW|intrin.h|__m64_m_pmulhrw(_m64、_m64)\_ \_|
|[_m_pmulhuw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pmulhuw)|SSE|intrin.h|__m64_m_pmulhuw(_m64、_m64)\_ \_|
|[_m_pmulhw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pmulhw)|MMX|intrin.h|__m64_m_pmulhw(_m64、_m64)\_ \_|
|[_m_pmullw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pmullw)|MMX|intrin.h|__m64_m_pmullw(_m64、_m64)\_ \_|
|[_m_por](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_por)|MMX|intrin.h|__m64_m_por(_m64、_m64)\_ \_|
|_m_prefetch|3DNOW|intrin.h|不合法_m_prefetch\*(不合法 )|
|_m_prefetchw|3DNOW|intrin.h|不合法_m_prefetchw(\*不合法 )|
|[_m_psadbw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psadbw)|SSE|intrin.h|__m64_m_psadbw(_m64、_m64)\_ \_|
|[_m_pshufw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pshufw)|SSE|intrin.h|__m64_m_pshufw(_m64\_|
|[_m_pslld](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pslld)|MMX|intrin.h|__m64_m_pslld(_m64、_m64)\_ \_|
|[_m_pslldi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pslldi)|MMX|intrin.h|__m64_m_pslldi(_m64,int)\_|
|[_m_psllq](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psllq)|MMX|intrin.h|__m64_m_psllq(_m64、_m64)\_ \_|
|[_m_psllqi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psllqi)|MMX|intrin.h|__m64_m_psllqi(_m64,\_國際)|
|[_m_psllw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psllw)|MMX|intrin.h|__m64_m_psllw(_m64、_m64)\_ \_|
|[_m_psllwi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psllwi)|MMX|intrin.h|__m64_m_psllwi(_m64,int)\_|
|[_m_psrad](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psrad)|MMX|intrin.h|__m64_m_psrad(_m64、_m64)\_ \_|
|[_m_psradi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psradi)|MMX|intrin.h|__m64_m_psradi(_m64,int)\_|
|[_m_psraw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psraw)|MMX|intrin.h|__m64_m_psraw(_m64、_m64)\_ \_|
|[_m_psrawi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psrawi)|MMX|intrin.h|__m64_m_psrawi(_m64\_|
|[_m_psrld](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psrld)|MMX|intrin.h|__m64_m_psrld(_m64、_m64)\_ \_|
|[_m_psrldi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psrldi)|MMX|intrin.h|__m64_m_psrldi(_m64,int)\_|
|[_m_psrlq](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psrlq)|MMX|intrin.h|__m64_m_psrlq(_m64、_m64)\_ \_|
|[_m_psrlqi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psrlqi)|MMX|intrin.h|__m64_m_psrlqi(_m64\_|
|[_m_psrlw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psrlw)|MMX|intrin.h|__m64_m_psrlw(_m64、_m64)\_ \_|
|[_m_psrlwi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psrlwi)|MMX|intrin.h|__m64_m_psrlwi(_m64\_|
|[_m_psubb](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psubb)|MMX|intrin.h|__m64_m_psubb(_m64、_m64)\_ \_|
|[_m_psubd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psubd)|MMX|intrin.h|__m64_m_psubd(_m64、_m64)\_ \_|
|[_m_psubsb](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psubsb)|MMX|intrin.h|__m64_m_psubsb(_m64、_m64)\_ \_|
|[_m_psubsw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psubsw)|MMX|intrin.h|__m64_m_psubsw(_m64、_m64)\_ \_|
|[_m_psubusb](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psubusb)|MMX|intrin.h|__m64_m_psubusb(_m64、_m64)\_ \_|
|[_m_psubusw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psubusw)|MMX|intrin.h|__m64_m_psubusw(_m64、_m64)\_ \_|
|[_m_psubw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psubw)|MMX|intrin.h|__m64_m_psubw(_m64、_m64)\_ \_|
|_m_pswapd|3DNOWEXT|intrin.h|__m64_m_pswapd(_m64)\_|
|[_m_punpckhbw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_punpckhbw)|MMX|intrin.h|__m64_m_punpckhbw(_m64、_m64)\_ \_|
|[_m_punpckhdq](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_punpckhdq)|MMX|intrin.h|__m64_m_punpckhdq(_m64、_m64)\_ \_|
|[_m_punpckhwd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_punpckhwd)|MMX|intrin.h|__m64_m_punpckhwd(_m64、_m64)\_ \_|
|[_m_punpcklbw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_punpcklbw)|MMX|intrin.h|__m64_m_punpcklbw(_m64、_m64)\_ \_|
|[_m_punpckldq](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_punpckldq)|MMX|intrin.h|__m64_m_punpckldq(_m64、_m64)\_ \_|
|[_m_punpcklwd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_punpcklwd)|MMX|intrin.h|__m64_m_punpcklwd(_m64、_m64)\_ \_|
|[_m_pxor](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pxor)|MMX|intrin.h|__m64_m_pxor(_m64、_m64)\_ \_|
|_m_to_float|3DNOW|intrin.h|浮動_m_to_float(_m64)\_|
|[_m_to_int](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_to_int)|MMX|intrin.h|_m_to_int(_m64)\_|
|[_mm_abs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_abs_epi16)|SSSE3|intrin.h|__m128i_mm_abs_epi16(_m128i)\_|
|[_mm_abs_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_abs_epi32)|SSSE3|intrin.h|__m128i_mm_abs_epi32(_m128i)\_|
|[_mm_abs_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_abs_epi8)|SSSE3|intrin.h|__m128i_mm_abs_epi8(_m128i)\_|
|[_mm_abs_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_abs_pi16)|SSSE3|intrin.h|__m64_mm_abs_pi16(_m64)\_|
|[_mm_abs_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_abs_pi32)|SSSE3|intrin.h|__m64_mm_abs_pi32(_m64)\_|
|[_mm_abs_pi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_abs_pi8)|SSSE3|intrin.h|__m64_mm_abs_pi8(_m64)\_|
|[_mm_add_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_add_epi16)|SSE2|intrin.h|__m128i_mm_add_epi16(_m128i、_m128i)\_ \_|
|[_mm_add_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_add_epi32)|SSE2|intrin.h|__m128i_mm_add_epi32(_m128i、_m128i)\_ \_|
|[_mm_add_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_add_epi64)|SSE2|intrin.h|__m128i_mm_add_epi64(_m128i、_m128i)\_ \_|
|[_mm_add_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_add_epi8)|SSE2|intrin.h|__m128i_mm_add_epi8(_m128i、_m128i)\_ \_|
|[_mm_add_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_add_pd)|SSE2|intrin.h|__m128d_mm_add_pd(_m128d、_m128d)\_ \_|
|[_mm_add_pi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_add_pi8)|MMX|mmintrin.h|__m64_mm_add_pi8(_m64、_m64)\_ \_[3]|
|[_mm_add_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_add_pi16)|MMX|mmintrin.h|__m64_mm_add_pi16(_m64、_m64)\_ \_[3]|
|[_mm_add_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_add_pi32)|MMX|mmintrin.h|__m64_mm_add_pi32(_m64、_m64)\_ \_[3]|
|[_mm_add_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_add_ps)|SSE|intrin.h|__m128_mm_add_ps(_m128、_m128)\_ \_|
|[_mm_add_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_add_sd)|SSE2|intrin.h|__m128d_mm_add_sd(_m128d、_m128d)\_ \_|
|[_mm_add_si64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_add_si64)|SSE2|intrin.h|__m64_mm_add_si64(_m64、_m64)\_ \_|
|[_mm_add_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_add_ss)|SSE|intrin.h|__m128_mm_add_ss(_m128、_m128)\_ \_|
|[_mm_adds_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_adds_epi16)|SSE2|intrin.h|__m128i_mm_adds_epi16(_m128i、_m128i)\_ \_|
|[_mm_adds_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_adds_epi8)|SSE2|intrin.h|__m128i_mm_adds_epi8(_m128i、_m128i)\_ \_|
|[_mm_adds_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_adds_epu16)|SSE2|intrin.h|__m128i_mm_adds_epu16(_m128i、_m128i)\_ \_|
|[_mm_adds_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_adds_epu8)|SSE2|intrin.h|__m128i_mm_adds_epu8(_m128i、_m128i)\_ \_|
|[_mm_adds_pi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_adds_pi8)|MMX|mmintrin.h|__m64_mm_adds_pi8(_m64,_m64)\_ \_[3]|
|[_mm_adds_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_adds_pi16)|MMX|mmintrin.h|__m64_mm_adds_pi16(_m64、_m64)\_ \_[3]|
|[_mm_adds_pu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_adds_pu8)|MMX|mmintrin.h|__m64_mm_adds_pu8(_m64、_m64)\_ \_[3]|
|[_mm_adds_pu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_adds_pu16)|MMX|mmintrin.h|__m64_mm_adds_pu16(_m64、_m64)\_ \_[3]|
|[_mm_addsub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_addsub_pd)|SSE3|intrin.h|__m128d_mm_addsub_pd(_m128d、_m128d)\_ \_|
|[_mm_addsub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_addsub_ps)|SSE3|intrin.h|__m128_mm_addsub_ps(_m128、_m128)\_ \_|
|[_mm_aesdec_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_aesdec_si128)|AESNI [2]|immintrin.h|__m128i_mm_aesdec_si128(_m128i、_m128i)\_ \_|
|[_mm_aesdeclast_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_aesdeclast_si128)|AESNI [2]|immintrin.h|__m128i_mm_aesdeclast_si128(_m128i、_m128i)\_ \_|
|[_mm_aesenc_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_aesenc_si128)|AESNI [2]|immintrin.h|__m128i_mm_aesenc_si128(_m128i、_m128i)\_ \_|
|[_mm_aesenclast_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_aesenclast_si128)|AESNI [2]|immintrin.h|__m128i_mm_aesenclast_si128(_m128i、_m128i)\_ \_|
|[_mm_aesimc_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_aesimc_si128)|AESNI [2]|immintrin.h|__m128i_mm_aesimc_si128(_m128i)\_|
|[_mm_aeskeygenassist_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_aeskeygenassist_si128)|AESNI [2]|immintrin.h|__m128i_mm_aeskeygenassist_si128(_m128i,\_康斯特)|
|[_mm_alignr_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_alignr_epi8)|SSSE3|intrin.h|__m128i_mm_alignr_epi8(_m128i、_m128i、\_\_國際)|
|[_mm_alignr_pi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_alignr_pi8)|SSSE3|intrin.h|__m64_mm_alignr_pi8(_m64、_m64、\_\_國際)|
|[_mm_and_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_and_pd)|SSE2|intrin.h|__m128d_mm_and_pd(_m128d、_m128d)\_ \_|
|[_mm_and_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_and_ps)|SSE|intrin.h|__m128_mm_and_ps(_m128、_m128)\_ \_|
|[_mm_and_si64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_and_si64)|MMX|mmintrin.h|__m64_mm_and_si64(_m64、_m64)\_ \_[3]|
|[_mm_and_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_and_si128)|SSE2|intrin.h|__m128i_mm_and_si128(_m128i、_m128i)\_ \_|
|[_mm_andnot_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_andnot_pd)|SSE2|intrin.h|__m128d_mm_andnot_pd(_m128d、_m128d)\_ \_|
|[_mm_andnot_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_andnot_ps)|SSE|intrin.h|__m128_mm_andnot_ps(_m128、_m128)\_ \_|
|[_mm_andnot_si64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_andnot_si64)|MMX|mmintrin.h|__m64_mm_andnot_si64(_m64、_m64)\_ \_[3]|
|[_mm_andnot_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_andnot_si128)|SSE2|intrin.h|__m128i_mm_andnot_si128(_m128i、_m128i)\_ \_|
|[_mm_avg_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_avg_epu16)|SSE2|intrin.h|__m128i_mm_avg_epu16(_m128i、_m128i)\_ \_|
|[_mm_avg_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_avg_epu8)|SSE2|intrin.h|__m128i_mm_avg_epu8(_m128i、_m128i)\_ \_|
|[_mm_blend_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_blend_epi16)|SSE41|intrin.h|__m128i_mm_blend_epi16(_m128i、_m128i、\_\_康斯特)|
|[_mm_blend_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_blend_epi32)|AVX2 [2]|immintrin.h|__m128i_mm_blend_epi32(_m128i、_m128i、\_\_康斯特)|
|[_mm_blend_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_blend_pd)|SSE41|intrin.h|__m128d_mm_blend_pd(_m128d、_m128d、\_\_康斯特)|
|[_mm_blend_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_blend_ps)|SSE41|intrin.h|__m128_mm_blend_ps(_m128、_m128、\_\_康斯特)|
|[_mm_blendv_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_blendv_epi8)|SSE41|intrin.h|__m128i_mm_blendv_epi8(_m128i、_m128i、_m128i)\_ \_ \_|
|[_mm_blendv_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_blendv_pd)|SSE41|intrin.h|__m128d_mm_blendv_pd(_m128d、_m128d、_m128d)\_ \_ \_|
|[_mm_blendv_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_blendv_ps)|SSE41|intrin.h|__m128_mm_blendv_ps(_m128、_m128、_m128)\_ \_ \_|
|[_mm_broadcast_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_broadcast_ss)|AVX [2]|immintrin.h|__m128 _mm_broadcast_ss(float const *)|
|[_mm_broadcastb_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_broadcastb_epi8)|AVX2 [2]|immintrin.h|__m128i_mm_broadcastb_epi8(_m128i)\_|
|[_mm_broadcastd_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_broadcastd_epi32)|AVX2 [2]|immintrin.h|__m128i_mm_broadcastd_epi32(_m128i)\_|
|[_mm_broadcastq_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_broadcastq_epi64)|AVX2 [2]|immintrin.h|__m128i_mm_broadcastq_epi64(_m128i)\_|
|[_mm_broadcastsd_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_broadcastsd_pd)|AVX2 [2]|immintrin.h|__m128d_mm_broadcastsd_pd(_m128d)\_|
|[_mm_broadcastss_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_broadcastss_ps)|AVX2 [2]|immintrin.h|__m128_mm_broadcastss_ps(_m128)\_|
|[_mm_broadcastw_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_broadcastw_epi16)|AVX2 [2]|immintrin.h|__m128i_mm_broadcastw_epi16(_m128i)\_|
|[_mm_castpd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_castpd_ps)|SSSE3|intrin.h|__m128_mm_castpd_ps(_m128d)\_|
|[_mm_castpd_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_castpd_si128)|SSSE3|intrin.h|__m128i_mm_castpd_si128(_m128d)\_|
|[_mm_castps_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_castps_pd)|SSSE3|intrin.h|__m128d_mm_castps_pd(_m128)\_|
|[_mm_castps_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_castps_si128)|SSSE3|intrin.h|__m128i_mm_castps_si128(_m128)\_|
|[_mm_castsi128_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_castsi128_pd)|SSSE3|intrin.h|__m128d_mm_castsi128_pd(_m128i)\_|
|[_mm_castsi128_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_castsi128_ps)|SSSE3|intrin.h|__m128_mm_castsi128_ps(_m128i)\_|
|[_mm_clflush](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_clflush)|SSE2|intrin.h|空_mm_clflush(空孔\*)|
|[_mm_clmulepi64_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_clmulepi64_si128)|PCLMULQDQ [2]|immintrin.h|__m128i_mm_clmulepi64_si128(_m128i、_m128i、\_\_康斯特)|
|_mm_cmov_si128|XOP [1]|ammintrin.h|__m128i_mm_cmov_si128(_m128i、_m128i、_m128i)\_ \_ \_|
|[_mm_cmp_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmp_pd)|AVX [2]|immintrin.h|__m128d_mm_cmp_pd(_m128d、_m128d、\_\_康斯特)|
|[_mm_cmp_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmp_ps)|AVX [2]|immintrin.h|__m128_mm_cmp_ps(_m128、_m128、\_\_康斯特)|
|[_mm_cmp_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmp_sd)|AVX [2]|immintrin.h|__m128d_mm_cmp_sd(_m128d、_m128d、\_\_康斯特)|
|[_mm_cmp_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmp_ss)|AVX [2]|immintrin.h|__m128_mm_cmp_ss(_m128、_m128、\_\_康斯特)|
|[_mm_cmpeq_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpeq_epi16)|SSE2|intrin.h|__m128i_mm_cmpeq_epi16(_m128i、_m128i)\_ \_|
|[_mm_cmpeq_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpeq_epi32)|SSE2|intrin.h|__m128i_mm_cmpeq_epi32(_m128i、_m128i)\_ \_|
|[_mm_cmpeq_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpeq_epi64)|SSE41|intrin.h|__m128i_mm_cmpeq_epi64(_m128i、_m128i)\_ \_|
|[_mm_cmpeq_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpeq_epi8)|SSE2|intrin.h|__m128i_mm_cmpeq_epi8(_m128i、_m128i)\_ \_|
|[_mm_cmpeq_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpeq_pd)|SSE2|intrin.h|__m128d_mm_cmpeq_pd(_m128d、_m128d)\_ \_|
|[_mm_cmpeq_pi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpeq_pi8)|MMX|mmintrin.h|__m64_mm_cmpeq_pi8(_m64、_m64)\_ \_[3]|
|[_mm_cmpeq_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpeq_pi16)|MMX|mmintrin.h|__m64_mm_cmpeq_pi16(_m64、_m64)\_ \_[3]|
|[_mm_cmpeq_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpeq_pi32)|MMX|mmintrin.h|__m64_mm_cmpeq_pi32(_m64,_m64)\_ \_[3]|
|[_mm_cmpeq_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpeq_ps)|SSE|intrin.h|__m128_mm_cmpeq_ps(_m128、_m128)\_ \_|
|[_mm_cmpeq_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpeq_sd)|SSE2|intrin.h|__m128d_mm_cmpeq_sd(_m128d、_m128d)\_ \_|
|[_mm_cmpeq_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpeq_ss)|SSE|intrin.h|__m128_mm_cmpeq_ss(_m128、_m128)\_ \_|
|[_mm_cmpestra](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpestra)|SSE42|intrin.h|int _mm_cmpestra(_m128i、int、_m128i、int、const\_ \_int)|
|[_mm_cmpestrc](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpestrc)|SSE42|intrin.h|_mm_cmpestrc(_m128i、int、_m128i、int、const\_ \_int)|
|[_mm_cmpestri](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpestri)|SSE42|intrin.h|_mm_cmpestri(_m128i、int、_m128i、int、const\_ \_int)|
|[_mm_cmpestrm](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpestrm)|SSE42|intrin.h|__m128i_mm_cmpestrm(_m128i、int、_m128i、int、const\_ \_int)|
|[_mm_cmpestro](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpestro)|SSE42|intrin.h|_mm_cmpestro(_m128i、int、_m128i、int、const\_ \_int)|
|[_mm_cmpestrs](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpestrs)|SSE42|intrin.h|_mm_cmpestrs(_m128i、int、_m128i、int、const\_ \_int)|
|[_mm_cmpestrz](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpestrz)|SSE42|intrin.h|_mm_cmpestrz(_m128i、int、_m128i、int、const\_ \_int)|
|[_mm_cmpge_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpge_pd)|SSE2|intrin.h|__m128d_mm_cmpge_pd(_m128d、_m128d)\_ \_|
|[_mm_cmpge_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpge_ps)|SSE|intrin.h|__m128_mm_cmpge_ps(_m128、_m128)\_ \_|
|[_mm_cmpge_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpge_sd)|SSE2|intrin.h|__m128d_mm_cmpge_sd(_m128d、_m128d)\_ \_|
|[_mm_cmpge_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpge_ss)|SSE|intrin.h|__m128_mm_cmpge_ss(_m128、_m128)\_ \_|
|[_mm_cmpgt_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpgt_epi16)|SSE2|intrin.h|__m128i_mm_cmpgt_epi16(_m128i、_m128i)\_ \_|
|[_mm_cmpgt_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpgt_epi32)|SSE2|intrin.h|__m128i_mm_cmpgt_epi32(_m128i、_m128i)\_ \_|
|[_mm_cmpgt_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpgt_epi64)|SSE42|intrin.h|__m128i_mm_cmpgt_epi64(_m128i、_m128i)\_ \_|
|[_mm_cmpgt_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpgt_epi8)|SSE2|intrin.h|__m128i_mm_cmpgt_epi8(_m128i、_m128i)\_ \_|
|[_mm_cmpgt_pi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpgt_pi8)|MMX|mmintrin.h|__m64_mm_cmpgt_pi8(_m64、_m64)\_ \_[3]|
|[_mm_cmpgt_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpgt_pi16)|MMX|mmintrin.h|__m64_mm_cmpgt_pi16(_m64、_m64)\_ \_[3]|
|[_mm_cmpgt_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpgt_pi32)|MMX|mmintrin.h|__m64_mm_cmpgt_pi32(_m64、_m64)\_ \_[3]|
|[_mm_cmpgt_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpgt_pd)|SSE2|intrin.h|__m128d_mm_cmpgt_pd(_m128d、_m128d)\_ \_|
|[_mm_cmpgt_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpgt_ps)|SSE|intrin.h|__m128_mm_cmpgt_ps(_m128、_m128)\_ \_|
|[_mm_cmpgt_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpgt_sd)|SSE2|intrin.h|__m128d_mm_cmpgt_sd(_m128d、_m128d)\_ \_|
|[_mm_cmpgt_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpgt_ss)|SSE|intrin.h|__m128_mm_cmpgt_ss(_m128、_m128)\_ \_|
|[_mm_cmpistra](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpistra)|SSE42|intrin.h|\__mm_cmpistra(_m128i、_m128i、\_康斯特)|
|[_mm_cmpistrc](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpistrc)|SSE42|intrin.h|\__mm_cmpistrc(_m128i、_m128i、\_康斯特)|
|[_mm_cmpistri](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpistri)|SSE42|intrin.h|\__mm_cmpistri(_m128i、_m128i、\_康斯特)|
|[_mm_cmpistrm](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpistrm)|SSE42|intrin.h|__m128i_mm_cmpistrm(_m128i、_m128i、\_\_康斯特)|
|[_mm_cmpistro](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpistro)|SSE42|intrin.h|\__mm_cmpistro(_m128i、_m128i、\_康斯特)|
|[_mm_cmpistrs](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpistrs)|SSE42|intrin.h|\__mm_cmpistrs(_m128i、_m128i、\_康斯特)|
|[_mm_cmpistrz](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpistrz)|SSE42|intrin.h|\__mm_cmpistrz(_m128i、_m128i、\_康斯特)|
|[_mm_cmple_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmple_pd)|SSE2|intrin.h|__m128d_mm_cmple_pd(_m128d、_m128d)\_ \_|
|[_mm_cmple_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmple_ps)|SSE|intrin.h|__m128_mm_cmple_ps(_m128、_m128)\_ \_|
|[_mm_cmple_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmple_sd)|SSE2|intrin.h|__m128d_mm_cmple_sd(_m128d、_m128d)\_ \_|
|[_mm_cmple_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmple_ss)|SSE|intrin.h|__m128_mm_cmple_ss(_m128、_m128)\_ \_|
|[_mm_cmplt_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmplt_epi16)|SSE2|intrin.h|__m128i_mm_cmplt_epi16(_m128i,_m128i)\_ \_|
|[_mm_cmplt_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmplt_epi32)|SSE2|intrin.h|__m128i_mm_cmplt_epi32(_m128i、_m128i)\_ \_|
|[_mm_cmplt_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmplt_epi8)|SSE2|intrin.h|__m128i_mm_cmplt_epi8(_m128i、_m128i)\_ \_|
|[_mm_cmplt_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmplt_pd)|SSE2|intrin.h|__m128d_mm_cmplt_pd(_m128d、_m128d)\_ \_|
|[_mm_cmplt_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmplt_ps)|SSE|intrin.h|__m128_mm_cmplt_ps(_m128、_m128)\_ \_|
|[_mm_cmplt_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmplt_sd)|SSE2|intrin.h|__m128d_mm_cmplt_sd(_m128d、_m128d)\_ \_|
|[_mm_cmplt_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmplt_ss)|SSE|intrin.h|__m128_mm_cmplt_ss(_m128、_m128)\_ \_|
|[_mm_cmpneq_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpneq_pd)|SSE2|intrin.h|__m128d_mm_cmpneq_pd(_m128d、_m128d)\_ \_|
|[_mm_cmpneq_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpneq_ps)|SSE|intrin.h|__m128_mm_cmpneq_ps(_m128、_m128)\_ \_|
|[_mm_cmpneq_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpneq_sd)|SSE2|intrin.h|__m128d_mm_cmpneq_sd(_m128d、_m128d)\_ \_|
|[_mm_cmpneq_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpneq_ss)|SSE|intrin.h|__m128_mm_cmpneq_ss(_m128、_m128)\_ \_|
|[_mm_cmpnge_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnge_pd)|SSE2|intrin.h|__m128d_mm_cmpnge_pd(_m128d、_m128d)\_ \_|
|[_mm_cmpnge_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnge_ps)|SSE|intrin.h|__m128_mm_cmpnge_ps(_m128、_m128)\_ \_|
|[_mm_cmpnge_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnge_sd)|SSE2|intrin.h|__m128d_mm_cmpnge_sd(_m128d、_m128d)\_ \_|
|[_mm_cmpnge_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnge_ss)|SSE|intrin.h|__m128_mm_cmpnge_ss(_m128,_m128)\_ \_|
|[_mm_cmpngt_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpngt_pd)|SSE2|intrin.h|__m128d_mm_cmpngt_pd(_m128d、_m128d)\_ \_|
|[_mm_cmpngt_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpngt_ps)|SSE|intrin.h|__m128_mm_cmpngt_ps(_m128、_m128)\_ \_|
|[_mm_cmpngt_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpngt_sd)|SSE2|intrin.h|__m128d_mm_cmpngt_sd(_m128d、_m128d)\_ \_|
|[_mm_cmpngt_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpngt_ss)|SSE|intrin.h|__m128_mm_cmpngt_ss(_m128、_m128)\_ \_|
|[_mm_cmpnle_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnle_pd)|SSE2|intrin.h|__m128d_mm_cmpnle_pd(_m128d、_m128d)\_ \_|
|[_mm_cmpnle_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnle_ps)|SSE|intrin.h|__m128_mm_cmpnle_ps(_m128、_m128)\_ \_|
|[_mm_cmpnle_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnle_sd)|SSE2|intrin.h|__m128d_mm_cmpnle_sd(_m128d,_m128d)\_ \_|
|[_mm_cmpnle_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnle_ss)|SSE|intrin.h|__m128_mm_cmpnle_ss(_m128、_m128)\_ \_|
|[_mm_cmpnlt_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnlt_pd)|SSE2|intrin.h|__m128d_mm_cmpnlt_pd(_m128d、_m128d)\_ \_|
|[_mm_cmpnlt_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnlt_ps)|SSE|intrin.h|__m128_mm_cmpnlt_ps(_m128、_m128)\_ \_|
|[_mm_cmpnlt_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnlt_sd)|SSE2|intrin.h|__m128d_mm_cmpnlt_sd(_m128d,_m128d)\_ \_|
|[_mm_cmpnlt_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnlt_ss)|SSE|intrin.h|__m128_mm_cmpnlt_ss(_m128、_m128)\_ \_|
|[_mm_cmpord_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpord_pd)|SSE2|intrin.h|__m128d_mm_cmpord_pd(_m128d、_m128d)\_ \_|
|[_mm_cmpord_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpord_ps)|SSE|intrin.h|__m128_mm_cmpord_ps(_m128、_m128)\_ \_|
|[_mm_cmpord_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpord_sd)|SSE2|intrin.h|__m128d_mm_cmpord_sd(_m128d、_m128d)\_ \_|
|[_mm_cmpord_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpord_ss)|SSE|intrin.h|__m128_mm_cmpord_ss(_m128、_m128)\_ \_|
|[_mm_cmpunord_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpunord_pd)|SSE2|intrin.h|__m128d_mm_cmpunord_pd(_m128d、_m128d)\_ \_|
|[_mm_cmpunord_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpunord_ps)|SSE|intrin.h|__m128_mm_cmpunord_ps(_m128、_m128)\_ \_|
|[_mm_cmpunord_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpunord_sd)|SSE2|intrin.h|__m128d_mm_cmpunord_sd(_m128d、_m128d)\_ \_|
|[_mm_cmpunord_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpunord_ss)|SSE|intrin.h|__m128_mm_cmpunord_ss(_m128、_m128)\_ \_|
|_mm_com_epi16|XOP [1]|ammintrin.h|__m128i_mm_com_epi16(_m128i、_m128i、\_\_國際)|
|_mm_com_epi32|XOP [1]|ammintrin.h|__m128i_mm_com_epi32(_m128i、_m128i、\_\_內)|
|_mm_com_epi64|XOP [1]|ammintrin.h|__m128i_mm_com_epi32(_m128i、_m128i、\_\_內)|
|_mm_com_epi8|XOP [1]|ammintrin.h|__m128i_mm_com_epi8(_m128i、_m128i、\_\_國際)|
|_mm_com_epu16|XOP [1]|ammintrin.h|__m128i_mm_com_epu16(_m128i、_m128i、\_\_國際)|
|_mm_com_epu32|XOP [1]|ammintrin.h|__m128i_mm_com_epu32(_m128i、_m128i、\_\_國際)|
|_mm_com_epu64|XOP [1]|ammintrin.h|__m128i_mm_com_epu32(_m128i、_m128i、\_\_國際)|
|_mm_com_epu8|XOP [1]|ammintrin.h|__m128i_mm_com_epu8(_m128i、_m128i、\_\_國際)|
|[_mm_comieq_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comieq_sd)|SSE2|intrin.h|\__mm_comieq_sd(_m128d,_m128d) \_|
|[_mm_comieq_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comieq_ss)|SSE|intrin.h|\__mm_comieq_ss(_m128,_m128) \_|
|[_mm_comige_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comige_sd)|SSE2|intrin.h|\__mm_comige_sd(_m128d,_m128d) \_|
|[_mm_comige_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comige_ss)|SSE|intrin.h|\__mm_comige_ss(_m128,_m128) \_|
|[_mm_comigt_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comigt_sd)|SSE2|intrin.h|\__mm_comigt_sd(_m128d,_m128d) \_|
|[_mm_comigt_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comigt_ss)|SSE|intrin.h|\__mm_comigt_ss(_m128,_m128) \_|
|[_mm_comile_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comile_sd)|SSE2|intrin.h|\__mm_comile_sd(_m128d,_m128d) \_|
|[_mm_comile_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comile_ss)|SSE|intrin.h|\__mm_comile_ss(_m128、_m128) \_|
|[_mm_comilt_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comilt_sd)|SSE2|intrin.h|\__mm_comilt_sd(_m128d,_m128d) \_|
|[_mm_comilt_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comilt_ss)|SSE|intrin.h|\__mm_comilt_ss(_m128,_m128) \_|
|[_mm_comineq_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comineq_sd)|SSE2|intrin.h|\__mm_comineq_sd(_m128d,_m128d) \_|
|[_mm_comineq_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comineq_ss)|SSE|intrin.h|\__mm_comineq_ss(_m128,_m128) \_|
|[_mm_crc32_u16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_crc32_u16)|SSE42|intrin.h|無符號int_mm_crc32_u16(無符號int,無符號短)|
|[_mm_crc32_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_crc32_u32)|SSE42|intrin.h|無符號 int _mm_crc32_u32(無符號 int,無符號 int)|
|[_mm_crc32_u8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_crc32_u8)|SSE42|intrin.h|無符號的int_mm_crc32_u8(無符號int,無符號字元)|
|[_mm_cvt_pi2ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvt_pi2ps)|SSE|intrin.h|__m128_mm_cvt_pi2ps(_m128、_m64)\_ \_|
|[_mm_cvt_ps2pi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvt_ps2pi)|SSE|intrin.h|__m64_mm_cvt_ps2pi(_m128)\_|
|[_mm_cvt_si2ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvt_si2ss)|SSE|intrin.h|__m128_mm_cvt_si2ss(_m128,\_國際)|
|[_mm_cvt_ss2si](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvt_ss2si)|SSE|intrin.h|_mm_cvt_ss2si(_m128)\_|
|[_mm_cvtepi16_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepi16_epi32)|SSE41|intrin.h|__m128i_mm_cvtepi16_epi32(_m128i)\_|
|[_mm_cvtepi16_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepi16_epi64)|SSE41|intrin.h|__m128i_mm_cvtepi16_epi64(_m128i)\_|
|[_mm_cvtepi32_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepi32_epi64)|SSE41|intrin.h|__m128i_mm_cvtepi32_epi64(_m128i)\_|
|[_mm_cvtepi32_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepi32_pd)|SSE2|intrin.h|__m128d_mm_cvtepi32_pd(_m128i)\_|
|[_mm_cvtepi32_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepi32_ps)|SSE2|intrin.h|__m128_mm_cvtepi32_ps(_m128i)\_|
|[_mm_cvtepi8_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepi8_epi16)|SSE41|intrin.h|__m128i_mm_cvtepi8_epi16(_m128i)\_|
|[_mm_cvtepi8_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepi8_epi32)|SSE41|intrin.h|__m128i_mm_cvtepi8_epi32(_m128i)\_|
|[_mm_cvtepi8_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepi8_epi64)|SSE41|intrin.h|__m128i_mm_cvtepi8_epi64(_m128i)\_|
|[_mm_cvtepu16_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepu16_epi32)|SSE41|intrin.h|__m128i_mm_cvtepu16_epi32(_m128i)\_|
|[_mm_cvtepu16_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepu16_epi64)|SSE41|intrin.h|__m128i_mm_cvtepu16_epi64(_m128i)\_|
|[_mm_cvtepu32_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepu32_epi64)|SSE41|intrin.h|__m128i_mm_cvtepu32_epi64(_m128i)\_|
|[_mm_cvtepu8_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepu8_epi16)|SSE41|intrin.h|__m128i_mm_cvtepu8_epi16(_m128i)\_|
|[_mm_cvtepu8_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepu8_epi32)|SSE41|intrin.h|__m128i_mm_cvtepu8_epi32(_m128i)\_|
|[_mm_cvtepu8_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepu8_epi64)|SSE41|intrin.h|__m128i_mm_cvtepu8_epi64(_m128i)\_|
|[_mm_cvtpd_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtpd_epi32)|SSE2|intrin.h|__m128i_mm_cvtpd_epi32(_m128d)\_|
|[_mm_cvtpd_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtpd_pi32)|SSE2|intrin.h|__m64_mm_cvtpd_pi32(_m128d)\_|
|[_mm_cvtpd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtpd_ps)|SSE2|intrin.h|__m128_mm_cvtpd_ps(_m128d)\_|
|[_mm_cvtph_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtph_ps)|F16C [2]|immintrin.h|__m128_mm_cvtph_ps(_m128i)\_|
|[_mm_cvtpi32_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtpi32_pd)|SSE2|intrin.h|__m128d_mm_cvtpi32_pd(_m64)\_|
|[_mm_cvtps_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtps_epi32)|SSE2|intrin.h|__m128i_mm_cvtps_epi32(_m128)\_|
|[_mm_cvtps_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtps_pd)|SSE2|intrin.h|__m128d_mm_cvtps_pd(_m128)\_|
|[_mm_cvtps_ph](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtps_ph)|F16C [2]|immintrin.h|__m128i_mm_cvtps_ph(_m128,\_康斯特)|
|[_mm_cvtsd_f64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtsd_f64)|SSSE3|intrin.h|雙_mm_cvtsd_f64(_m128d)\_|
|[_mm_cvtsd_si32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtsd_si32)|SSE2|intrin.h|_mm_cvtsd_si32(_m128d)\_|
|[_mm_cvtsd_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtsd_ss)|SSE2|intrin.h|__m128_mm_cvtsd_ss(_m128、_m128d)\_ \_|
|[_mm_cvtsi128_si32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtsi128_si32)|SSE2|intrin.h|_mm_cvtsi128_si32(_m128i)\_|
|[_mm_cvtsi32_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtsi32_sd)|SSE2|intrin.h|__m128d_mm_cvtsi32_sd(_m128d,int)\_|
|[_mm_cvtsi32_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtsi32_si128)|SSE2|intrin.h|__m128i _mm_cvtsi32_si128(int)|
|[_mm_cvtsi32_si64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtsi32_si64)|MMX|mmintrin.h|__m64_mm_cvtsi32_si64(int) [3]|
|[_mm_cvtsi64_si32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtsi64_si32)|MMX|mmintrin.h|_mm_cvtsi64_si32 (__m64) [3]|
|[_mm_cvtss_f32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtss_f32)|SSSE3|intrin.h|浮_mm_cvtss_f32(_m128)\_|
|[_mm_cvtss_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtss_sd)|SSE2|intrin.h|__m128d_mm_cvtss_sd(_m128d、_m128)\_ \_|
|[_mm_cvtt_ps2pi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtt_ps2pi)|SSE|intrin.h|__m64_mm_cvtt_ps2pi(_m128)\_|
|[_mm_cvtt_ss2si](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtt_ss2si)|SSE|intrin.h|_mm_cvtt_ss2si(_m128)\_|
|[_mm_cvttpd_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvttpd_epi32)|SSE2|intrin.h|__m128i_mm_cvttpd_epi32(_m128d)\_|
|[_mm_cvttpd_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvttpd_pi32)|SSE2|intrin.h|__m64_mm_cvttpd_pi32(_m128d)\_|
|[_mm_cvttps_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvttps_epi32)|SSE2|intrin.h|__m128i_mm_cvttps_epi32(_m128)\_|
|[_mm_cvttsd_si32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvttsd_si32)|SSE2|intrin.h|_mm_cvttsd_si32(_m128d)\_|
|[_mm_div_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_div_pd)|SSE2|intrin.h|__m128d_mm_div_pd(_m128d、_m128d)\_ \_|
|[_mm_div_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_div_ps)|SSE|intrin.h|__m128_mm_div_ps(_m128、_m128)\_ \_|
|[_mm_div_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_div_sd)|SSE2|intrin.h|__m128d_mm_div_sd(_m128d,_m128d)\_ \_|
|[_mm_div_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_div_ss)|SSE|intrin.h|__m128_mm_div_ss(_m128、_m128)\_ \_|
|[_mm_dp_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_dp_pd)|SSE41|intrin.h|__m128d_mm_dp_pd(_m128d、_m128d、\_\_康斯特)|
|[_mm_dp_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_dp_ps)|SSE41|intrin.h|__m128_mm_dp_ps(_m128、_m128、\_\_康斯特)|
|[_mm_empty](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_empty)|MMX|mmintrin.h|空_mm_empty (空) [3]|
|[_mm_extract_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_extract_epi16)|SSE2|intrin.h|_mm_extract_epi16(_m128i,int)\_|
|[_mm_extract_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_extract_epi32)|SSE41|intrin.h|_mm_extract_epi32(_m128i,\_康斯特)|
|[_mm_extract_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_extract_epi8)|SSE41|intrin.h|_mm_extract_epi8(_m128i,\_康斯特)|
|[_mm_extract_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_extract_ps)|SSE41|intrin.h|int _mm_extract_ps(_m128,\_康斯特)|
|[_mm_extract_si64](mm-extract-si64-mm-extracti-si64.md)|SSE4a|intrin.h|__m128i_mm_extract_si64(_m128i,_m128i)\_ \_|
|[_mm_extracti_si64](mm-extract-si64-mm-extracti-si64.md)|SSE4a|intrin.h|__m128i_mm_extracti_si64(_m128i、int、int)\_|
|[_mm_fmadd_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmadd_pd)|FMA [2]|immintrin.h|__m128d_mm_fmadd_pd(_m128d、_m128d、_m128d)\_ \_ \_|
|[_mm_fmadd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmadd_ps)|FMA [2]|immintrin.h|__m128_mm_fmadd_ps(_m128、_m128、_m128)\_ \_ \_|
|[_mm_fmadd_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmadd_sd)|FMA [2]|immintrin.h|__m128d_mm_fmadd_sd(_m128d、_m128d、_m128d)\_ \_ \_|
|[_mm_fmadd_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmadd_ss)|FMA [2]|immintrin.h|__m128_mm_fmadd_ss(_m128、_m128、_m128)\_ \_ \_|
|[_mm_fmaddsub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmaddsub_pd)|FMA [2]|immintrin.h|__m128d_mm_fmaddsub_pd(_m128d、_m128d、_m128d)\_ \_ \_|
|[_mm_fmaddsub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmaddsub_ps)|FMA [2]|immintrin.h|__m128_mm_fmaddsub_ps(_m128、_m128、_m128)\_ \_ \_|
|[_mm_fmsub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmsub_pd)|FMA [2]|immintrin.h|__m128d_mm_fmsub_pd(_m128d、_m128d、_m128d)\_ \_ \_|
|[_mm_fmsub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmsub_ps)|FMA [2]|immintrin.h|__m128_mm_fmsub_ps(_m128、_m128、_m128)\_ \_ \_|
|[_mm_fmsub_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmsub_sd)|FMA [2]|immintrin.h|__m128d_mm_fmsub_sd(_m128d、_m128d、_m128d)\_ \_ \_|
|[_mm_fmsub_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmsub_ss)|FMA [2]|immintrin.h|__m128_mm_fmsub_ss(_m128、_m128、_m128)\_ \_ \_|
|[_mm_fmsubadd_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmsubadd_pd)|FMA [2]|immintrin.h|__m128d_mm_fmsubadd_pd(_m128d、_m128d、_m128d)\_ \_ \_|
|[_mm_fmsubadd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmsubadd_ps)|FMA [2]|immintrin.h|__m128_mm_fmsubadd_ps(_m128、_m128、_m128)\_ \_ \_|
|[_mm_fnmadd_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fnmadd_pd)|FMA [2]|immintrin.h|__m128d_mm_fnmadd_pd(_m128d、_m128d、_m128d)\_ \_ \_|
|[_mm_fnmadd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fnmadd_ps)|FMA [2]|immintrin.h|__m128_mm_fnmadd_ps(_m128、_m128、_m128)\_ \_ \_|
|[_mm_fnmadd_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fnmadd_sd)|FMA [2]|immintrin.h|__m128d_mm_fnmadd_sd(_m128d、_m128d、_m128d)\_ \_ \_|
|[_mm_fnmadd_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fnmadd_ss)|FMA [2]|immintrin.h|__m128_mm_fnmadd_ss(_m128、_m128、_m128)\_ \_ \_|
|[_mm_fnmsub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fnmsub_pd)|FMA [2]|immintrin.h|__m128d_mm_fnmsub_pd(_m128d、_m128d、_m128d)\_ \_ \_|
|[_mm_fnmsub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fnmsub_ps)|FMA [2]|immintrin.h|__m128_mm_fnmsub_ps(_m128、_m128、_m128)\_ \_ \_|
|[_mm_fnmsub_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fnmsub_sd)|FMA [2]|immintrin.h|__m128d_mm_fnmsub_sd(_m128d、_m128d、_m128d)\_ \_ \_|
|[_mm_fnmsub_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fnmsub_ss)|FMA [2]|immintrin.h|__m128_mm_fnmsub_ss(_m128、_m128、_m128)\_ \_ \_|
|_mm_frcz_pd|XOP [1]|ammintrin.h|__m128d_mm_frcz_pd(_m128d)\_|
|_mm_frcz_ps|XOP [1]|ammintrin.h|__m128_mm_frcz_ps(_m128)\_|
|_mm_frcz_sd|XOP [1]|ammintrin.h|__m128d_mm_frcz_sd(_m128d、_m128d)\_ \_|
|_mm_frcz_ss|XOP [1]|ammintrin.h|__m128_mm_frcz_ss(_m128、_m128)\_ \_|
|[_mm_getcsr](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_getcsr)|SSE|intrin.h|unsigned int _mm_getcsr(void)|
|[_mm_hadd_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hadd_epi16)|SSSE3|intrin.h|__m128i_mm_hadd_epi16(_m128i、_m128i)\_ \_|
|[_mm_hadd_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hadd_epi32)|SSSE3|intrin.h|__m128i_mm_hadd_epi32(_m128i、_m128i)\_ \_|
|[_mm_hadd_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hadd_pd)|SSE3|intrin.h|__m128d_mm_hadd_pd(_m128d、_m128d)\_ \_|
|[_mm_hadd_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hadd_pi16)|SSSE3|intrin.h|__m64_mm_hadd_pi16(_m64、_m64)\_ \_|
|[_mm_hadd_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hadd_pi32)|SSSE3|intrin.h|__m64_mm_hadd_pi32(_m64、_m64)\_ \_|
|[_mm_hadd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hadd_ps)|SSE3|intrin.h|__m128_mm_hadd_ps(_m128、_m128)\_ \_|
|_mm_haddd_epi16|XOP [1]|ammintrin.h|__m128i_mm_haddd_epi16(_m128i)\_|
|_mm_haddd_epi8|XOP [1]|ammintrin.h|__m128i_mm_haddd_epi8(_m128i)\_|
|_mm_haddd_epu16|XOP [1]|ammintrin.h|__m128i_mm_haddd_epu16(_m128i)\_|
|_mm_haddd_epu8|XOP [1]|ammintrin.h|__m128i_mm_haddd_epu8(_m128i)\_|
|_mm_haddq_epi16|XOP [1]|ammintrin.h|__m128i_mm_haddq_epi16(_m128i)\_|
|_mm_haddq_epi32|XOP [1]|ammintrin.h|__m128i_mm_haddq_epi32(_m128i)\_|
|_mm_haddq_epi8|XOP [1]|ammintrin.h|__m128i_mm_haddq_epi8(_m128i)\_|
|_mm_haddq_epu16|XOP [1]|ammintrin.h|__m128i_mm_haddq_epu16(_m128i)\_|
|_mm_haddq_epu32|XOP [1]|ammintrin.h|__m128i_mm_haddq_epu32(_m128i)\_|
|_mm_haddq_epu8|XOP [1]|ammintrin.h|__m128i_mm_haddq_epu8(_m128i)\_|
|[_mm_hadds_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hadds_epi16)|SSSE3|intrin.h|__m128i_mm_hadds_epi16(_m128i、_m128i)\_ \_|
|[_mm_hadds_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hadds_pi16)|SSSE3|intrin.h|__m64_mm_hadds_pi16(_m64、_m64)\_ \_|
|_mm_haddw_epi8|XOP [1]|ammintrin.h|__m128i_mm_haddw_epi8(_m128i)\_|
|_mm_haddw_epu8|XOP [1]|ammintrin.h|__m128i_mm_haddw_epu8(_m128i)\_|
|[_mm_hsub_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hsub_epi16)|SSSE3|intrin.h|__m128i_mm_hsub_epi16(_m128i、_m128i)\_ \_|
|[_mm_hsub_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hsub_epi32)|SSSE3|intrin.h|__m128i_mm_hsub_epi32(_m128i,_m128i)\_ \_|
|[_mm_hsub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hsub_pd)|SSE3|intrin.h|__m128d_mm_hsub_pd(_m128d、_m128d)\_ \_|
|[_mm_hsub_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hsub_pi16)|SSSE3|intrin.h|__m64_mm_hsub_pi16(_m64、_m64)\_ \_|
|[_mm_hsub_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hsub_pi32)|SSSE3|intrin.h|__m64_mm_hsub_pi32(_m64、_m64)\_ \_|
|[_mm_hsub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hsub_ps)|SSE3|intrin.h|__m128_mm_hsub_ps(_m128、_m128)\_ \_|
|_mm_hsubd_epi16|XOP [1]|ammintrin.h|__m128i_mm_hsubd_epi16(_m128i)\_|
|_mm_hsubq_epi32|XOP [1]|ammintrin.h|__m128i_mm_hsubq_epi32(_m128i)\_|
|[_mm_hsubs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hsubs_epi16)|SSSE3|intrin.h|__m128i_mm_hsubs_epi16(_m128i、_m128i)\_ \_|
|[_mm_hsubs_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hsubs_pi16)|SSSE3|intrin.h|__m64_mm_hsubs_pi16(_m64、_m64)\_ \_|
|_mm_hsubw_epi8|XOP [1]|ammintrin.h|__m128i_mm_hsubw_epi8(_m128i)\_|
|[_mm_i32gather_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_i32gather_epi32)|AVX2 [2]|immintrin.h|__m128i_mm_i32gather_epi32(int const, \* \__m128i, const int)|
|[_mm_i32gather_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_i32gather_epi64)|AVX2 [2]|immintrin.h|__m128i_mm_i32gather_epi64(_int64,_m128i,\_\*康斯特\_)|
|[_mm_i32gather_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_i32gather_pd)|AVX2 [2]|immintrin.h|__m128d_mm_i32gather_pd(雙錐\*,_m128i,\_康斯特)|
|[_mm_i32gather_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_i32gather_ps)|AVX2 [2]|immintrin.h|__m128_mm_i32gather_ps(浮點\*、_m128i、\_康斯特)|
|[_mm_i64gather_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_i64gather_epi32)|AVX2 [2]|immintrin.h|__m128i_mm_i64gather_epi32(int const,_m128i,const \* \_int)|
|[_mm_i64gather_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_i64gather_epi64)|AVX2 [2]|immintrin.h|\*__m128i_mm_i64gather_epi64(_int64,_m128i,\_\_康斯特)|
|[_mm_i64gather_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_i64gather_pd)|AVX2 [2]|immintrin.h|__m128d_mm_i64gather_pd(雙錐\*,_m128i,const \_int)|
|[_mm_i64gather_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_i64gather_ps)|AVX2 [2]|immintrin.h|__m128_mm_i64gather_ps(浮式康\*\_斯特 ,_m128i,康斯特)|
|[_mm_insert_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_insert_epi16)|SSE2|intrin.h|__m128i_mm_insert_epi16(_m128i、int、int)\_|
|[_mm_insert_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_insert_epi32)|SSE41|intrin.h|__m128i_mm_insert_epi32(_m128i、int、const\_int)|
|[_mm_insert_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_insert_epi8)|SSE41|intrin.h|__m128i_mm_insert_epi8(_m128i、int、const\_int)|
|[_mm_insert_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_insert_ps)|SSE41|intrin.h|__m128_mm_insert_ps(_m128、_m128、\_\_康斯特)|
|[_mm_insert_si64](mm-insert-si64-mm-inserti-si64.md)|SSE4a|intrin.h|__m128i_mm_insert_si64(_m128i、_m128i)\_ \_|
|[_mm_inserti_si64](mm-insert-si64-mm-inserti-si64.md)|SSE4a|intrin.h|__m128i_mm_inserti_si64(_m128i、_m128i、int、int)\_ \_|
|[_mm_lddqu_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_lddqu_si128)|SSE3|intrin.h|\*__m128i_mm_lddqu_si128(_m128i)\_|
|[_mm_lfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_lfence)|SSE2|intrin.h|void _mm_lfence(void)|
|[_mm_load_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_load_pd)|SSE2|intrin.h|__m128d_mm_load_pd(雙\*)|
|[_mm_load_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_load_ps)|SSE|intrin.h|__m128_mm_load_ps(浮動\*)|
|[_mm_load_ps1](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_load_ps1)|SSE|intrin.h|__m128_mm_load_ps1(浮動\*)|
|[_mm_load_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_load_sd)|SSE2|intrin.h|__m128d_mm_load_sd(雙\*)|
|[_mm_load_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_load_si128)|SSE2|intrin.h|\___m128i_mm_load_si128(_m128i\*)|
|[_mm_load_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_load_ss)|SSE|intrin.h|__m128_mm_load_ss(浮動\*)|
|[_mm_load1_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_load1_pd)|SSE2|intrin.h|__m128d_mm_load1_pd(雙\*)|
|[_mm_loaddup_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loaddup_pd)|SSE3|intrin.h|__m128d_mm_loaddup_pd(雙錐\*)|
|[_mm_loadh_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loadh_pd)|SSE2|intrin.h|__m128d_mm_loadh_pd(_m128d、\_\*雙 )|
|[_mm_loadh_pi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loadh_pi)|SSE|intrin.h|__m128_mm_loadh_pi(_m128、_m64)\_ \_ \*|
|[_mm_loadl_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loadl_epi64)|SSE2|intrin.h|__m128i_mm_loadl_epi64(\_\*_m128i )|
|[_mm_loadl_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loadl_pd)|SSE2|intrin.h|__m128d_mm_loadl_pd(_m128d、\_\*雙 )|
|[_mm_loadl_pi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loadl_pi)|SSE|intrin.h|__m128_mm_loadl_pi(_m128、_m64)\_ \_ \*|
|[_mm_loadr_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loadr_pd)|SSE2|intrin.h|__m128d_mm_loadr_pd(雙\*)|
|[_mm_loadr_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loadr_ps)|SSE|intrin.h|__m128_mm_loadr_ps(浮動\*)|
|[_mm_loadu_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loadu_pd)|SSE2|intrin.h|__m128d_mm_loadu_pd(雙\*)|
|[_mm_loadu_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loadu_ps)|SSE|intrin.h|__m128_mm_loadu_ps(浮動\*)|
|[_mm_loadu_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loadu_si128)|SSE2|intrin.h|__m128i_mm_loadu_si128(\_\*_m128i )|
|_mm_macc_epi16|XOP [1]|ammintrin.h|__m128i_mm_macc_epi16(_m128i、_m128i、_m128i)\_ \_ \_|
|_mm_macc_epi32|XOP [1]|ammintrin.h|__m128i_mm_macc_epi32(_m128i、_m128i、_m128i)\_ \_ \_|
|_mm_macc_pd|FMA4 [1]|ammintrin.h|__m128d_mm_macc_pd(_m128d、_m128d、_m128d)\_ \_ \_|
|_mm_macc_ps|FMA4 [1]|ammintrin.h|__m128_mm_macc_ps(_m128、_m128、_m128)\_ \_ \_|
|_mm_macc_sd|FMA4 [1]|ammintrin.h|__m128d_mm_macc_sd(_m128d、_m128d、_m128d)\_ \_ \_|
|_mm_macc_ss|FMA4 [1]|ammintrin.h|__m128_mm_macc_ss(_m128、_m128、_m128)\_ \_ \_|
|_mm_maccd_epi16|XOP [1]|ammintrin.h|__m128i_mm_maccd_epi16(_m128i、_m128i、_m128i)\_ \_ \_|
|_mm_macchi_epi32|XOP [1]|ammintrin.h|__m128i_mm_macchi_epi32(_m128i、_m128i、_m128i)\_ \_ \_|
|_mm_macclo_epi32|XOP [1]|ammintrin.h|__m128i_mm_macclo_epi32(_m128i、_m128i、_m128i)\_ \_ \_|
|_mm_maccs_epi16|XOP [1]|ammintrin.h|__m128i_mm_maccs_epi16(_m128i、_m128i、_m128i)\_ \_ \_|
|_mm_maccs_epi32|XOP [1]|ammintrin.h|__m128i_mm_maccs_epi32(_m128i、_m128i、_m128i)\_ \_ \_|
|_mm_maccsd_epi16|XOP [1]|ammintrin.h|__m128i_mm_maccsd_epi16(_m128i、_m128i、_m128i)\_ \_ \_|
|_mm_maccshi_epi32|XOP [1]|ammintrin.h|__m128i_mm_maccshi_epi32(_m128i、_m128i、_m128i)\_ \_ \_|
|_mm_maccslo_epi32|XOP [1]|ammintrin.h|__m128i_mm_maccslo_epi32(_m128i、_m128i、_m128i)\_ \_ \_|
|[_mm_madd_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_madd_epi16)|SSE2|intrin.h|__m128i_mm_madd_epi16(_m128i、_m128i)\_ \_|
|[_mm_madd_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_madd_pi16)|MMX|mmintrin.h|__m64_mm_madd_pi16(_m64、_m64)\_ \_[3]|
|_mm_maddd_epi16|XOP [1]|ammintrin.h|__m128i_mm_maddd_epi16(_m128i、_m128i、_m128i)\_ \_ \_|
|_mm_maddsd_epi16|XOP [1]|ammintrin.h|__m128i_mm_maddsd_epi16(_m128i、_m128i、_m128i)\_ \_ \_|
|_mm_maddsub_pd|FMA4 [1]|ammintrin.h|__m128d_mm_maddsub_pd(_m128d、_m128d、_m128d)\_ \_ \_|
|_mm_maddsub_ps|FMA4 [1]|ammintrin.h|__m128_mm_maddsub_ps(_m128、_m128、_m128)\_ \_ \_|
|[_mm_maddubs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_maddubs_epi16)|SSSE3|intrin.h|__m128i_mm_maddubs_epi16(_m128i、_m128i)\_ \_|
|[_mm_maddubs_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_maddubs_pi16)|SSSE3|intrin.h|__m64_mm_maddubs_pi16(_m64、_m64)\_ \_|
|[_mm_mask_i32gather_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mask_i32gather_epi32)|AVX2 [2]|immintrin.h|\*__m128i_mm_mask_i32gather_epi32(_m128i、_m128i、_m128i、\_\_\_康斯特)|
|[_mm_mask_i32gather_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mask_i32gather_epi64)|AVX2 [2]|immintrin.h|\*__m128i_mm_mask_i32gather_epi64(_m128i、_int64、_m128i、_m128i、\_\_\_\_康斯特)|
|[_mm_mask_i32gather_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mask_i32gather_pd)|AVX2 [2]|immintrin.h|__m128d_mm_mask_i32gather_pd(_m128d、\_雙\*錐 、_m128i、_m128d、\_\_康斯特)|
|[_mm_mask_i32gather_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mask_i32gather_ps)|AVX2 [2]|immintrin.h|__m128_mm_mask_i32gather_ps(_m128、\_浮\*式 、_m128i、_m128、\_\_康斯特)|
|[_mm_mask_i64gather_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mask_i64gather_epi32)|AVX2 [2]|immintrin.h|\*__m128i_mm_mask_i64gather_epi32(_m128i、_m128i、_m128i、\_\_\_康斯特)|
|[_mm_mask_i64gather_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mask_i64gather_epi64)|AVX2 [2]|immintrin.h|\*__m128i_mm_mask_i64gather_epi64(_m128i、_int64、_m128i、_m128i、\_\_\_\_康斯特)|
|[_mm_mask_i64gather_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mask_i64gather_pd)|AVX2 [2]|immintrin.h|__m128d_mm_mask_i64gather_pd(_m128d、\_雙\*錐 、_m128i、_m128d、\_\_康斯特)|
|[_mm_mask_i64gather_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mask_i64gather_ps)|AVX2 [2]|immintrin.h|__m128_mm_mask_i64gather_ps(_m128、\_浮\*式 、_m128i、_m128、\_\_康斯特)|
|[_mm_maskload_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_maskload_epi32)|AVX2 [2]|immintrin.h|__m128i_mm_maskload_epi32(_m128i) \* \_|
|[_mm_maskload_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_maskload_epi64)|AVX2 [2]|immintrin.h|__m128i_mm_maskload_epi64(_int64\_康\*斯特 ,_m128i) \_|
|[_mm_maskload_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_maskload_pd)|AVX [2]|immintrin.h|__m128d_mm_maskload_pd(雙錐\*,_m128i) \_|
|[_mm_maskload_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_maskload_ps)|AVX [2]|immintrin.h|__m128_mm_maskload_ps(浮點\*,_m128i) \_|
|[_mm_maskmoveu_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_maskmoveu_si128)|SSE2|intrin.h|空_mm_maskmoveu_si128(_m128i、_m128i、\_\_焦\*炭 )|
|[_mm_maskstore_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_maskstore_epi32)|AVX2 [2]|immintrin.h|空_mm_maskstore_epi32(因\*,_m128i,_m128i) \_ \_|
|[_mm_maskstore_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_maskstore_epi64)|AVX2 [2]|immintrin.h|無效_mm_maskstore_epi64(_int64、_m128i、_m128i)\_ \* \_ \_|
|[_mm_maskstore_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_maskstore_pd)|AVX [2]|immintrin.h|空_mm_maskstore_pd(雙\*,_m128i,_m128d) \_ \_|
|[_mm_maskstore_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_maskstore_ps)|AVX [2]|immintrin.h|空_mm_maskstore_ps(浮\*子\_、_m128i、_m128) \_|
|[_mm_max_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_max_epi16)|SSE2|intrin.h|__m128i_mm_max_epi16(_m128i、_m128i)\_ \_|
|[_mm_max_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_max_epi32)|SSE41|intrin.h|__m128i_mm_max_epi32(_m128i、_m128i)\_ \_|
|[_mm_max_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_max_epi8)|SSE41|intrin.h|__m128i_mm_max_epi8(_m128i、_m128i)\_ \_|
|[_mm_max_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_max_epu16)|SSE41|intrin.h|__m128i_mm_max_epu16(_m128i、_m128i)\_ \_|
|[_mm_max_epu32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_max_epu32)|SSE41|intrin.h|__m128i_mm_max_epu32(_m128i、_m128i)\_ \_|
|[_mm_max_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_max_epu8)|SSE2|intrin.h|__m128i_mm_max_epu8(_m128i、_m128i)\_ \_|
|[_mm_max_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_max_pd)|SSE2|intrin.h|__m128d_mm_max_pd(_m128d、_m128d)\_ \_|
|[_mm_max_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_max_ps)|SSE|intrin.h|__m128_mm_max_ps(_m128,_m128)\_ \_|
|[_mm_max_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_max_sd)|SSE2|intrin.h|__m128d_mm_max_sd(_m128d、_m128d)\_ \_|
|[_mm_max_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_max_ss)|SSE|intrin.h|__m128_mm_max_ss(_m128、_m128)\_ \_|
|[_mm_mfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mfence)|SSE2|intrin.h|void _mm_mfence(void)|
|[_mm_min_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_min_epi16)|SSE2|intrin.h|__m128i_mm_min_epi16(_m128i、_m128i)\_ \_|
|[_mm_min_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_min_epi32)|SSE41|intrin.h|__m128i_mm_min_epi32(_m128i、_m128i)\_ \_|
|[_mm_min_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_min_epi8)|SSE41|intrin.h|__m128i_mm_min_epi8(_m128i、_m128i)\_ \_|
|[_mm_min_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_min_epu16)|SSE41|intrin.h|__m128i_mm_min_epu16(_m128i、_m128i)\_ \_|
|[_mm_min_epu32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_min_epu32)|SSE41|intrin.h|__m128i_mm_min_epu32(_m128i、_m128i)\_ \_|
|[_mm_min_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_min_epu8)|SSE2|intrin.h|\___m128i_mm_min_epu8(_m128i_m128i)\_|
|[_mm_min_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_min_pd)|SSE2|intrin.h|__m128d_mm_min_pd(_m128d、_m128d)\_ \_|
|[_mm_min_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_min_ps)|SSE|intrin.h|__m128_mm_min_ps(_m128、_m128)\_ \_|
|[_mm_min_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_min_sd)|SSE2|intrin.h|__m128d_mm_min_sd(_m128d、_m128d)\_ \_|
|[_mm_min_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_min_ss)|SSE|intrin.h|__m128_mm_min_ss(_m128、_m128)\_ \_|
|[_mm_minpos_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_minpos_epu16)|SSE41|intrin.h|__m128i_mm_minpos_epu16(_m128i)\_|
|[_mm_monitor](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_monitor)|SSE3|intrin.h|無效_mm_monitor(不合法 const*,無符號 int,無符號 int)|
|[_mm_move_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_move_epi64)|SSE2|intrin.h|__m128i_mm_move_epi64(_m128i)\_|
|[_mm_move_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_move_sd)|SSE2|intrin.h|__m128d_mm_move_sd(_m128d、_m128d)\_ \_|
|[_mm_move_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_move_ss)|SSE|intrin.h|__m128_mm_move_ss(_m128,_m128)\_ \_|
|[_mm_movedup_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_movedup_pd)|SSE3|intrin.h|__m128d_mm_movedup_pd(_m128d)\_|
|[_mm_movehdup_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_movehdup_ps)|SSE3|intrin.h|__m128_mm_movehdup_ps(_m128)\_|
|[_mm_movehl_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_movehl_ps)|SSE|intrin.h|__m128_mm_movehl_ps(_m128、_m128)\_ \_|
|[_mm_moveldup_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_moveldup_ps)|SSE3|intrin.h|__m128_mm_moveldup_ps(_m128)\_|
|[_mm_movelh_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_movelh_ps)|SSE|intrin.h|__m128_mm_movelh_ps(_m128、_m128)\_ \_|
|[_mm_movemask_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_movemask_epi8)|SSE2|intrin.h|_mm_movemask_epi8(_m128i)\_|
|[_mm_movemask_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_movemask_pd)|SSE2|intrin.h|_mm_movemask_pd(_m128d)\_|
|[_mm_movemask_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_movemask_ps)|SSE|intrin.h|_mm_movemask_ps(_m128)\_|
|[_mm_movepi64_pi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_movepi64_pi64)|SSE2|intrin.h|__m64_mm_movepi64_pi64(_m128i)\_|
|[_mm_movpi64_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_movpi64_epi64)|SSE2|intrin.h|__m128i_mm_movpi64_epi64(_m64)\_|
|[_mm_mpsadbw_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mpsadbw_epu8)|SSE41|intrin.h|__m128i_mm_mpsadbw_epu8(_m128i、_m128i、\_\_康斯特)|
|_mm_msub_pd|FMA4 [1]|ammintrin.h|__m128d_mm_msub_pd(_m128d、_m128d、_m128d)\_ \_ \_|
|_mm_msub_ps|FMA4 [1]|ammintrin.h|__m128_mm_msub_ps(_m128、_m128、_m128)\_ \_ \_|
|_mm_msub_sd|FMA4 [1]|ammintrin.h|__m128d_mm_msub_sd(_m128d、_m128d、_m128d)\_ \_ \_|
|_mm_msub_ss|FMA4 [1]|ammintrin.h|__m128_mm_msub_ss(_m128、_m128、_m128)\_ \_ \_|
|_mm_msubadd_pd|FMA4 [1]|ammintrin.h|__m128d_mm_msubadd_pd(_m128d、_m128d、_m128d)\_ \_ \_|
|_mm_msubadd_ps|FMA4 [1]|ammintrin.h|__m128_mm_msubadd_ps(_m128、_m128、_m128)\_ \_ \_|
|[_mm_mul_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mul_epi32)|SSE41|intrin.h|__m128i_mm_mul_epi32(_m128i、_m128i)\_ \_|
|[_mm_mul_epu32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mul_epu32)|SSE2|intrin.h|__m128i_mm_mul_epu32(_m128i、_m128i)\_ \_|
|[_mm_mul_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mul_pd)|SSE2|intrin.h|__m128d_mm_mul_pd(_m128d、_m128d)\_ \_|
|[_mm_mul_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mul_ps)|SSE|intrin.h|__m128_mm_mul_ps(_m128、_m128)\_ \_|
|[_mm_mul_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mul_sd)|SSE2|intrin.h|__m128d_mm_mul_sd(_m128d、_m128d)\_ \_|
|[_mm_mul_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mul_ss)|SSE|intrin.h|__m128_mm_mul_ss(_m128、_m128)\_ \_|
|[_mm_mul_su32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mul_su32)|SSE2|intrin.h|__m64_mm_mul_su32(_m64,_m64)\_ \_|
|[_mm_mulhi_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mulhi_epi16)|SSE2|intrin.h|__m128i_mm_mulhi_epi16(_m128i、_m128i)\_ \_|
|[_mm_mulhi_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mulhi_epu16)|SSE2|intrin.h|__m128i_mm_mulhi_epu16(_m128i、_m128i)\_ \_|
|[_mm_mulhi_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mulhi_pi16)|MMX|mmintrin.h|__m64_mm_mulhi_pi16(_m64、_m64)[3]\_ \_|
|[_mm_mulhrs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mulhrs_epi16)|SSSE3|intrin.h|__m128i_mm_mulhrs_epi16(_m128i、_m128i)\_ \_|
|[_mm_mulhrs_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mulhrs_pi16)|SSSE3|intrin.h|__m64_mm_mulhrs_pi16(_m64、_m64)\_ \_|
|[_mm_mullo_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mullo_epi16)|SSE2|intrin.h|__m128i_mm_mullo_epi16(_m128i、_m128i)\_ \_|
|[_mm_mullo_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mullo_epi32)|SSE41|intrin.h|__m128i_mm_mullo_epi32(_m128i、_m128i)\_ \_|
|[_mm_mullo_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mullo_pi16)|MMX|mmintrin.h|__m64_mm_mullo_pi16(_m64、_m64)\_ \_[3]|
|[_mm_mwait](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mwait)|SSE3|intrin.h|不合法_mm_mwait(無符號 int,無符號 int)|
|_mm_nmacc_pd|FMA4 [1]|ammintrin.h|__m128d_mm_nmacc_pd(_m128d、_m128d、_m128d)\_ \_ \_|
|_mm_nmacc_ps|FMA4 [1]|ammintrin.h|__m128_mm_nmacc_ps(_m128、_m128、_m128)\_ \_ \_|
|_mm_nmacc_sd|FMA4 [1]|ammintrin.h|__m128d_mm_nmacc_sd(_m128d、_m128d、_m128d)\_ \_ \_|
|_mm_nmacc_ss|FMA4 [1]|ammintrin.h|__m128_mm_nmacc_ss(_m128、_m128、_m128)\_ \_ \_|
|_mm_nmsub_pd|FMA4 [1]|ammintrin.h|__m128d_mm_nmsub_pd(_m128d、_m128d、_m128d)\_ \_ \_|
|_mm_nmsub_ps|FMA4 [1]|ammintrin.h|__m128_mm_nmsub_ps(_m128、_m128、_m128)\_ \_ \_|
|_mm_nmsub_sd|FMA4 [1]|ammintrin.h|__m128d_mm_nmsub_sd(_m128d、_m128d、_m128d)\_ \_ \_|
|_mm_nmsub_ss|FMA4 [1]|ammintrin.h|__m128_mm_nmsub_ss(_m128、_m128、_m128)\_ \_ \_|
|[_mm_or_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_or_pd)|SSE2|intrin.h|__m128d_mm_or_pd(_m128d、_m128d)\_ \_|
|[_mm_or_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_or_ps)|SSE|intrin.h|__m128_mm_or_ps(_m128、_m128)\_ \_|
|[_mm_or_si64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_or_si64)|MMX|mmintrin.h|__m64_mm_or_si64(_m64、_m64)\_ \_[3]|
|[_mm_or_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_or_si128)|SSE2|intrin.h|__m128i_mm_or_si128(_m128i,_m128i)\_ \_|
|[_mm_packs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_packs_epi16)|SSE2|intrin.h|__m128i_mm_packs_epi16(_m128i、_m128i)\_ \_|
|[_mm_packs_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_packs_epi32)|SSE2|intrin.h|__m128i_mm_packs_epi32(_m128i、_m128i)\_ \_|
|[_mm_packs_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_packs_pi16)|MMX|mmintrin.h|__m64_mm_packs_pi16(__m64,__m64) [3]|
|[_mm_packs_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_packs_pi32)|MMX|mmintrin.h|__m64_mm_packs_pi32(__m64、__m64) [3]|
|[_mm_packs_pu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_packs_pu16)|MMX|mmintrin.h|__m64_mm_packs_pu16(__m64、__m64) [3]|
|[_mm_packus_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_packus_epi16)|SSE2|intrin.h|__m128i_mm_packus_epi16(_m128i、_m128i)\_ \_|
|[_mm_packus_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_packus_epi32)|SSE41|intrin.h|__m128i_mm_packus_epi32(_m128i、_m128i)\_ \_|
|[_mm_pause](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_pause)|SSE2|intrin.h|void _mm_pause(void)|
|_mm_perm_epi8|XOP [1]|ammintrin.h|__m128i_mm_perm_epi8(_m128i、_m128i、_m128i)\_ \_ \_|
|[_mm_permute_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_permute_pd)|AVX [2]|immintrin.h|__m128d_mm_permute_pd(_m128d,int)\_|
|[_mm_permute_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_permute_ps)|AVX [2]|immintrin.h|__m128_mm_permute_ps(_m128\_|
|_mm_permute2_pd|XOP [1]|ammintrin.h|__m128d_mm_permute2_pd(_m128d、_m128d、_m128i、\_\_\_國際)|
|_mm_permute2_ps|XOP [1]|ammintrin.h|__m128_mm_permute2_ps(_m128、_m128、_m128i、\_\_\_內)|
|[_mm_permutevar_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_permutevar_pd)|AVX [2]|immintrin.h|__m128d_mm_permutevar_pd(_m128d、_m128i)\_ \_|
|[_mm_permutevar_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_permutevar_ps)|AVX [2]|immintrin.h|__m128_mm_permutevar_ps(_m128、_m128i)\_ \_|
|[_mm_popcnt_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_popcnt_u32)|POPCNT|intrin.h|int _mm_popcnt_u32(unsigned int)|
|[_mm_prefetch](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_prefetch)|SSE|intrin.h|空白_mm_prefetch (字元, int)|
|[_mm_rcp_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_rcp_ps)|SSE|intrin.h|__m128_mm_rcp_ps(_m128)\_|
|[_mm_rcp_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_rcp_ss)|SSE|intrin.h|__m128_mm_rcp_ss(_m128)\_|
|_mm_rot_epi16|XOP [1]|ammintrin.h|__m128i_mm_rot_epi16(_m128i、_m128i)\_ \_|
|_mm_rot_epi32|XOP [1]|ammintrin.h|__m128i_mm_rot_epi32(_m128i、_m128i)\_ \_|
|_mm_rot_epi64|XOP [1]|ammintrin.h|__m128i_mm_rot_epi64(_m128i、_m128i)\_ \_|
|_mm_rot_epi8|XOP [1]|ammintrin.h|__m128i_mm_rot_epi8(_m128i、_m128i)\_ \_|
|_mm_roti_epi16|XOP [1]|ammintrin.h|__m128i_mm_rot_epi16(_m128i,int)\_|
|_mm_roti_epi32|XOP [1]|ammintrin.h|__m128i_mm_rot_epi32(_m128i,int)\_|
|_mm_roti_epi64|XOP [1]|ammintrin.h|__m128i_mm_rot_epi64(_m128i\_|
|_mm_roti_epi8|XOP [1]|ammintrin.h|__m128i_mm_rot_epi8(_m128i\_|
|[_mm_round_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_round_pd)|SSE41|intrin.h|__m128d_mm_round_pd(_m128d,\_康斯特)|
|[_mm_round_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_round_ps)|SSE41|intrin.h|__m128_mm_round_ps(_m128,\_康斯特)|
|[_mm_round_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_round_sd)|SSE41|intrin.h|__m128d_mm_round_sd(_m128d、_m128d、\_\_康斯特)|
|[_mm_round_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_round_ss)|SSE41|intrin.h|__m128_mm_round_ss(_m128、_m128、\_\_康斯特)|
|[_mm_rsqrt_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_rsqrt_ps)|SSE|intrin.h|__m128_mm_rsqrt_ps(_m128)\_|
|[_mm_rsqrt_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_rsqrt_ss)|SSE|intrin.h|__m128_mm_rsqrt_ss(_m128)\_|
|[_mm_sad_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sad_epu8)|SSE2|intrin.h|__m128i_mm_sad_epu8(_m128i、_m128i)\_ \_|
|[_mm_set_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_epi16)|SSE2|intrin.h|__m128i_mm_set_epi16(短、短、短、短、短、短)|
|[_mm_set_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_epi32)|SSE2|intrin.h|__m128i_mm_set_epi32(int、int、int、int)|
|[_mm_set_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_epi64)|SSE2|intrin.h|__m128i_mm_set_epi64(_m64、_m64)\_ \_|
|[_mm_set_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_epi8)|SSE2|intrin.h|__m128i _mm_set_epi8(char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char)|
|[_mm_set_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_pd)|SSE2|intrin.h|__m128d_mm_set_pd(雙、雙)|
|[_mm_set_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_pi16)|MMX|intrin.h|__m64_mm_set_pi16(短、短、短、 短)|
|[_mm_set_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_pi32)|MMX|intrin.h|__m64_mm_set_pi32(int, int)|
|[_mm_set_pi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_pi8)|MMX|intrin.h|__m64_mm_set_pi8(焦炭、焦炭、焦炭、焦炭、焦炭、焦炭、焦炭、焦炭))|
|[_mm_set_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_ps)|SSE|intrin.h|__m128_mm_set_ps(浮子、浮子、浮子、浮子)|
|[_mm_set_ps1](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_ps1)|SSE|intrin.h|__m128 _mm_set_ps1(float)|
|[_mm_set_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_sd)|SSE2|intrin.h|__m128d _mm_set_sd(double)|
|[_mm_set_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_ss)|SSE|intrin.h|__m128 _mm_set_ss(float)|
|[_mm_set1_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set1_epi16)|SSE2|intrin.h|__m128i _mm_set1_epi16(short)|
|[_mm_set1_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set1_epi32)|SSE2|intrin.h|__m128i _mm_set1_epi32(int)|
|[_mm_set1_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set1_epi64)|SSE2|intrin.h|__m128i_mm_set1_epi64(_m64)\_|
|[_mm_set1_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set1_epi8)|SSE2|intrin.h|__m128i _mm_set1_epi8(char)|
|[_mm_set1_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set1_pd)|SSE2|intrin.h|__m128d _mm_set1_pd(double)|
|[_mm_set1_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set1_pi16)|MMX|intrin.h|__m64 _mm_set1_pi16(short)|
|[_mm_set1_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set1_pi32)|MMX|intrin.h|__m64 _mm_set1_pi32(int)|
|[_mm_set1_pi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set1_pi8)|MMX|intrin.h|__m64 _mm_set1_pi8(char)|
|[_mm_setcsr](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setcsr)|SSE|intrin.h|void _mm_setcsr(unsigned int)|
|_mm_setl_epi64|SSE2|intrin.h|__m128i_mm_setl_epi64(_m128i)\_|
|[_mm_setr_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setr_epi16)|SSE2|intrin.h|__m128i_mm_setr_epi16(短、短、短、短、短、短)|
|[_mm_setr_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setr_epi32)|SSE2|intrin.h|__m128i_mm_setr_epi32(int、int、int、int)|
|[_mm_setr_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setr_epi64)|SSE2|intrin.h|__m128i_mm_setr_epi64(_m64、_m64)\_ \_|
|[_mm_setr_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setr_epi8)|SSE2|intrin.h|__m128i _mm_setr_epi8(char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char)|
|[_mm_setr_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setr_pd)|SSE2|intrin.h|__m128d_mm_setr_pd(雙、雙)|
|[_mm_setr_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setr_pi16)|MMX|intrin.h|__m64_mm_setr_pi16(短、短、短、短)|
|[_mm_setr_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setr_pi32)|MMX|intrin.h|__m64_mm_setr_pi32(int, int)|
|[_mm_setr_pi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setr_pi8)|MMX|intrin.h|__m64_mm_setr_pi8(焦炭、焦炭、焦炭、焦炭、焦炭、焦炭、焦炭、焦炭))|
|[_mm_setr_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setr_ps)|SSE|intrin.h|__m128_mm_setr_ps(浮子、浮子、浮子、浮子)|
|[_mm_setzero_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setzero_pd)|SSE2|intrin.h|__m128d _mm_setzero_pd(void)|
|[_mm_setzero_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setzero_ps)|SSE|intrin.h|__m128 _mm_setzero_ps(void)|
|[_mm_setzero_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setzero_si128)|SSE2|intrin.h|__m128i _mm_setzero_si128(void)|
|[_mm_setzero_si64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setzero_si64)|MMX|intrin.h|__m64 _mm_setzero_si64(void)|
|[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)|SSE|intrin.h|void _mm_sfence(void)|
|_mm_sha_epi16|XOP [1]|ammintrin.h|__m128i_mm_sha_epi16(_m128i、_m128i)\_ \_|
|_mm_sha_epi32|XOP [1]|ammintrin.h|__m128i_mm_sha_epi32(_m128i、_m128i)\_ \_|
|_mm_sha_epi64|XOP [1]|ammintrin.h|__m128i_mm_sha_epi64(_m128i、_m128i)\_ \_|
|_mm_sha_epi8|XOP [1]|ammintrin.h|__m128i_mm_sha_epi8(_m128i、_m128i)\_ \_|
|_mm_shl_epi16|XOP [1]|ammintrin.h|__m128i_mm_shl_epi16(_m128i、_m128i)\_ \_|
|_mm_shl_epi32|XOP [1]|ammintrin.h|__m128i_mm_shl_epi32(_m128i、_m128i)\_ \_|
|_mm_shl_epi64|XOP [1]|ammintrin.h|__m128i_mm_shl_epi64(_m128i、_m128i)\_ \_|
|_mm_shl_epi8|XOP [1]|ammintrin.h|__m128i_mm_shl_epi8(_m128i、_m128i)\_ \_|
|[_mm_shuffle_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_shuffle_epi32)|SSE2|intrin.h|__m128i_mm_shuffle_epi32(_m128i,\_國際)|
|[_mm_shuffle_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_shuffle_epi8)|SSSE3|intrin.h|__m128i_mm_shuffle_epi8(_m128i、_m128i)\_ \_|
|[_mm_shuffle_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_shuffle_pd)|SSE2|intrin.h|__m128d_mm_shuffle_pd(_m128d、_m128d、\_\_國際)|
|[_mm_shuffle_pi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_shuffle_pi8)|SSSE3|intrin.h|__m64_mm_shuffle_pi8(_m64、_m64)\_ \_|
|[_mm_shuffle_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_shuffle_ps)|SSE|intrin.h|__m128_mm_shuffle_ps(_m128、_m128、\_\_無符號的int)|
|[_mm_shufflehi_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_shufflehi_epi16)|SSE2|intrin.h|__m128i_mm_shufflehi_epi16(_m128i,int)\_|
|[_mm_shufflelo_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_shufflelo_epi16)|SSE2|intrin.h|__m128i_mm_shufflelo_epi16(_m128i,int)\_|
|[_mm_sign_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sign_epi16)|SSSE3|intrin.h|__m128i_mm_sign_epi16(_m128i、_m128i)\_ \_|
|[_mm_sign_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sign_epi32)|SSSE3|intrin.h|__m128i_mm_sign_epi32(_m128i、_m128i)\_ \_|
|[_mm_sign_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sign_epi8)|SSSE3|intrin.h|__m128i_mm_sign_epi8(_m128i、_m128i)\_ \_|
|[_mm_sign_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sign_pi16)|SSSE3|intrin.h|__m64_mm_sign_pi16(_m64、_m64)\_ \_|
|[_mm_sign_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sign_pi32)|SSSE3|intrin.h|__m64_mm_sign_pi32(_m64,_m64)\_ \_|
|[_mm_sign_pi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sign_pi8)|SSSE3|intrin.h|__m64_mm_sign_pi8(_m64、_m64)\_ \_|
|[_mm_sll_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sll_epi16)|SSE2|intrin.h|__m128i_mm_sll_epi16(_m128i、_m128i)\_ \_|
|[_mm_sll_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sll_epi32)|SSE2|intrin.h|__m128i_mm_sll_epi32(_m128i、_m128i)\_ \_|
|[_mm_sll_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sll_epi64)|SSE2|intrin.h|__m128i_mm_sll_epi64(_m128i、_m128i)\_ \_|
|[_mm_sll_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sll_pi16)|MMX|mmintrin.h|__m64_mm_sll_pi16(_m64,_m64)\_ \_[3]|
|[_mm_sll_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sll_pi32)|MMX|mmintrin.h|__m64_mm_sll_pi32(_m64、_m64)\_ \_[3]|
|[_mm_sll_si64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sll_si64)|MMX|mmintrin.h|__m64_mm_sll_si64(_m64、_m64)[3]\_ \_|
|[_mm_slli_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_slli_epi16)|SSE2|intrin.h|__m128i_mm_slli_epi16(_m128i\_|
|[_mm_slli_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_slli_epi32)|SSE2|intrin.h|__m128i_mm_slli_epi32(_m128i\_|
|[_mm_slli_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_slli_epi64)|SSE2|intrin.h|__m128i_mm_slli_epi64(_m128i\_|
|[_mm_slli_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_slli_pi16)|MMX|mmintrin.h|__m64_mm_slli_pi16(_m64,int)\_[3]|
|[_mm_slli_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_slli_pi32)|MMX|mmintrin.h|__m64_mm_slli_pi32(_m64,int)\_[3]|
|[_mm_slli_si64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_slli_si64)|MMX|mmintrin.h|__m64_mm_slli_si64(_m64,int)\_[3]|
|[_mm_slli_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_slli_si128)|SSE2|intrin.h|__m128i_mm_slli_si128(_m128i,int)\_|
|[_mm_sllv_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sllv_epi32)|AVX2 [2]|immintrin.h|__m128i_mm_sllv_epi32(_m128i、_m128i)\_ \_|
|[_mm_sllv_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sllv_epi64)|AVX2 [2]|immintrin.h|__m128i_mm_sllv_epi64(_m128i、_m128i)\_ \_|
|[_mm_sqrt_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sqrt_pd)|SSE2|intrin.h|__m128d_mm_sqrt_pd(_m128d)\_|
|[_mm_sqrt_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sqrt_ps)|SSE|intrin.h|__m128_mm_sqrt_ps(_m128)\_|
|[_mm_sqrt_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sqrt_sd)|SSE2|intrin.h|__m128d_mm_sqrt_sd(_m128d、_m128d)\_ \_|
|[_mm_sqrt_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sqrt_ss)|SSE|intrin.h|__m128_mm_sqrt_ss (_m128)\_|
|[_mm_sra_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sra_epi16)|SSE2|intrin.h|__m128i_mm_sra_epi16(_m128i、_m128i)\_ \_|
|[_mm_sra_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sra_epi32)|SSE2|intrin.h|__m128i_mm_sra_epi32(_m128i、_m128i)\_ \_|
|[_mm_sra_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sra_pi16)|MMX|mmintrin.h|__m64_mm_sra_pi16(_m64、_m64)\_ \_[3]|
|[_mm_sra_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sra_pi32)|MMX|mmintrin.h|__m64_mm_sra_pi32(_m64、_m64)\_ \_[3]|
|[_mm_srai_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srai_epi16)|SSE2|intrin.h|__m128i_mm_srai_epi16(_m128i,int)\_|
|[_mm_srai_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srai_epi32)|SSE2|intrin.h|__m128i_mm_srai_epi32(_m128i\_|
|[_mm_srai_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srai_pi16)|MMX|mmintrin.h|__m64_mm_srai_pi16(_m64,int)\_[3]|
|[_mm_srai_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srai_pi32)|MMX|mmintrin.h|__m64_mm_srai_pi32(_m64,int)\_[3]|
|[_mm_srav_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srav_epi32)|AVX2 [2]|immintrin.h|__m128i_mm_srav_epi32(_m128i、_m128i)\_ \_|
|[_mm_srl_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srl_epi16)|SSE2|intrin.h|__m128i_mm_srl_epi16(_m128i、_m128i)\_ \_|
|[_mm_srl_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srl_epi32)|SSE2|intrin.h|__m128i_mm_srl_epi32(_m128i,_m128i)\_ \_|
|[_mm_srl_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srl_epi64)|SSE2|intrin.h|__m128i_mm_srl_epi64(_m128i、_m128i)\_ \_|
|[_mm_srl_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srl_pi16)|MMX|mmintrin.h|__m64_mm_srl_pi16(_m64、_m64)\_ \_[3]|
|[_mm_srl_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srl_pi32)|MMX|mmintrin.h|__m64_mm_srl_pi32(_m64、_m64)\_ \_[3]|
|[_mm_srl_si64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srl_si64)|MMX|mmintrin.h|__m64_mm_srl_si64(_m64、_m64)\_ \_[3]|
|[_mm_srli_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srli_epi16)|SSE2|intrin.h|__m128i_mm_srli_epi16(_m128i\_|
|[_mm_srli_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srli_epi32)|SSE2|intrin.h|__m128i_mm_srli_epi32(_m128i,int)\_|
|[_mm_srli_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srli_epi64)|SSE2|intrin.h|__m128i_mm_srli_epi64(_m128i\_|
|[_mm_srli_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srli_pi16)|MMX|mmintrin.h|__m64_mm_srli_pi16(_m64,int)\_[3]|
|[_mm_srli_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srli_pi32)|MMX|mmintrin.h|__m64_mm_srli_pi32(_m64,int)\_[3]|
|[_mm_srli_si64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srli_si64)|MMX|mmintrin.h|__m64_mm_srli_si64(_m64,int)\_[3]|
|[_mm_srli_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srli_si128)|SSE2|intrin.h|__m128i_mm_srli_si128(_m128i\_|
|[_mm_srlv_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srlv_epi32)|AVX2 [2]|immintrin.h|__m128i_mm_srlv_epi32(_m128i、_m128i)\_ \_|
|[_mm_srlv_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srlv_epi64)|AVX2 [2]|immintrin.h|__m128i_mm_srlv_epi64(_m128i、_m128i)\_ \_|
|[_mm_store_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_pd)|SSE2|intrin.h|不合法_mm_store_pd(\*雙 ,_m128d) \_|
|[_mm_store_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_ps)|SSE|intrin.h|空_mm_store_ps(浮\*子\_,_m128)|
|[_mm_store_ps1](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_ps1)|SSE|intrin.h|空_mm_store_ps1(浮\*子\_,_m128)|
|[_mm_store_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_sd)|SSE2|intrin.h|空_mm_store_sd(雙\*,_m128d) \_|
|[_mm_store_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_si128)|SSE2|intrin.h|空_mm_store_si128(_m128i,_m128i)\_ \* \_|
|[_mm_store_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_ss)|SSE|intrin.h|空_mm_store_ss(浮\*子\_,_m128)|
|[_mm_store1_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store1_pd)|SSE2|intrin.h|空_mm_store1_pd(雙\*,_m128d) \_|
|[_mm_storeh_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_storeh_pd)|SSE2|intrin.h|無效_mm_storeh_pd(雙\*,_m128d) \_|
|[_mm_storeh_pi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_storeh_pi)|SSE|intrin.h|無效_mm_storeh_pi(_m64、_m128)\_ \* \_|
|[_mm_storel_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_storel_epi64)|SSE2|intrin.h|不合法_mm_storel_epi64(_m128i、_m128i)\_ \* \_|
|[_mm_storel_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_storel_pd)|SSE2|intrin.h|空_mm_storel_pd(雙\*,_m128d) \_|
|[_mm_storel_pi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_storel_pi)|SSE|intrin.h|不_mm_storel_pi合法 (_m64、_m128)\_ \* \_|
|[_mm_storer_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_storer_pd)|SSE2|intrin.h|空_mm_storer_pd(雙\*,_m128d) \_|
|[_mm_storer_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_storer_ps)|SSE|intrin.h|空_mm_storer_ps(浮\*子\_,_m128)|
|[_mm_storeu_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_storeu_pd)|SSE2|intrin.h|空_mm_storeu_pd(雙\*,_m128d) \_|
|[_mm_storeu_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_storeu_ps)|SSE|intrin.h|空_mm_storeu_ps(浮\*子\_,_m128)|
|[_mm_storeu_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_storeu_si128)|SSE2|intrin.h|空_mm_storeu_si128(_m128i,_m128i)\_ \* \_|
|[_mm_stream_load_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_load_si128)|SSE41|intrin.h|__m128i_mm_stream_load_si128(_m128i)\_ \*|
|[_mm_stream_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_pd)|SSE2|intrin.h|空_mm_stream_pd(雙\*,_m128d) \_|
|[_mm_stream_pi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_pi)|SSE|intrin.h|空_mm_stream_pi(_m64、_m64)\_ \* \_|
|[_mm_stream_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_ps)|SSE|intrin.h|空_mm_stream_ps(浮\*子\_,_m128)|
|[_mm_stream_sd](mm-stream-sd.md)|SSE4a|intrin.h|空_mm_stream_sd(雙\*,_m128d) \_|
|[_mm_stream_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_si128)|SSE2|intrin.h|無效_mm_stream_si128(_m128i、_m128i)\_ \* \_|
|[_mm_stream_si32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_si32)|SSE2|intrin.h|空_mm_stream_si32(int,\*int)|
|[_mm_stream_ss](mm-stream-ss.md)|SSE4a|intrin.h|空_mm_stream_ss(浮\*子\_,_m128)|
|[_mm_sub_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sub_epi16)|SSE2|intrin.h|__m128i_mm_sub_epi16(_m128i、_m128i)\_ \_|
|[_mm_sub_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sub_epi32)|SSE2|intrin.h|__m128i_mm_sub_epi32(_m128i、_m128i)\_ \_|
|[_mm_sub_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sub_epi64)|SSE2|intrin.h|__m128i_mm_sub_epi64(_m128i、_m128i)\_ \_|
|[_mm_sub_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sub_epi8)|SSE2|intrin.h|__m128i_mm_sub_epi8(_m128i、_m128i)\_ \_|
|[_mm_sub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sub_pd)|SSE2|intrin.h|__m128d_mm_sub_pd(_m128d、_m128d)\_ \_|
|[_mm_sub_pi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sub_pi8)|MMX|mmintrin.h|__m64_mm_sub_pi8(_m64,_m64)\_ \_[3]|
|[_mm_sub_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sub_pi16)|MMX|mmintrin.h|__m64_mm_sub_pi16(_m64、_m64)\_ \_[3]|
|[_mm_sub_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sub_pi32)|MMX|mmintrin.h|__m64_mm_sub_pi32(_m64、_m64)[3]\_ \_|
|[_mm_sub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sub_ps)|SSE|intrin.h|__m128_mm_sub_ps(_m128、_m128)\_ \_|
|[_mm_sub_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sub_sd)|SSE2|intrin.h|__m128d_mm_sub_sd(_m128d、_m128d)\_ \_|
|[_mm_sub_si64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sub_si64)|SSE2|intrin.h|__m64_mm_sub_si64(_m64、_m64)\_ \_|
|[_mm_sub_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sub_ss)|SSE|intrin.h|__m128_mm_sub_ss(_m128、_m128)\_ \_|
|[_mm_subs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_subs_epi16)|SSE2|intrin.h|__m128i_mm_subs_epi16(_m128i、_m128i)\_ \_|
|[_mm_subs_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_subs_epi8)|SSE2|intrin.h|__m128i_mm_subs_epi8(_m128i、_m128i)\_ \_|
|[_mm_subs_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_subs_epu16)|SSE2|intrin.h|__m128i_mm_subs_epu16(_m128i、_m128i)\_ \_|
|[_mm_subs_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_subs_epu8)|SSE2|intrin.h|__m128i_mm_subs_epu8(_m128i、_m128i)\_ \_|
|[_mm_subs_pi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_subs_pi8)|MMX|mmintrin.h|__m64_mm_subs_pi8(_m64、_m64)\_ \_[3]|
|[_mm_subs_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_subs_pi16)|MMX|mmintrin.h|__m64_mm_subs_pi16(_m64、_m64)\_ \_[3]|
|[_mm_subs_pu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_subs_pu8)|MMX|mmintrin.h|__m64_mm_subs_pu8(_m64、_m64)[3]\_ \_|
|[_mm_subs_pu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_subs_pu16)|MMX|mmintrin.h|__m64_mm_subs_pu16(_m64、_m64)\_ \_[3]|
|[_mm_testc_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_testc_pd)|AVX [2]|immintrin.h|\__mm_testc_pd(_m128d、_m128d) \_|
|[_mm_testc_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_testc_ps)|AVX [2]|immintrin.h|\__mm_testc_ps(_m128,_m128) \_|
|[_mm_testc_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_testc_si128)|SSE41|intrin.h|\__mm_testc_si128(_m128i、_m128i) \_|
|[_mm_testnzc_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_testnzc_pd)|AVX [2]|immintrin.h|\__mm_testnzc_pd(_m128d,_m128d) \_|
|[_mm_testnzc_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_testnzc_ps)|AVX [2]|immintrin.h|\__mm_testnzc_ps(_m128,_m128) \_|
|[_mm_testnzc_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_testnzc_si128)|SSE41|intrin.h|\__mm_testnzc_si128(_m128i,_m128i) \_|
|[_mm_testz_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_testz_pd)|AVX [2]|immintrin.h|\__mm_testz_pd(_m128d,_m128d) \_|
|[_mm_testz_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_testz_ps)|AVX [2]|immintrin.h|\__mm_testz_ps(_m128,_m128) \_|
|[_mm_testz_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_testz_si128)|SSE41|intrin.h|\__mm_testz_si128(_m128i,_m128i) \_|
|[_mm_ucomieq_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomieq_sd)|SSE2|intrin.h|\__mm_ucomieq_sd(_m128d,_m128d) \_|
|[_mm_ucomieq_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomieq_ss)|SSE|intrin.h|\__mm_ucomieq_ss(_m128,_m128) \_|
|[_mm_ucomige_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomige_sd)|SSE2|intrin.h|\__mm_ucomige_sd(_m128d,_m128d) \_|
|[_mm_ucomige_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomige_ss)|SSE|intrin.h|\__mm_ucomige_ss(_m128,_m128) \_|
|[_mm_ucomigt_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomigt_sd)|SSE2|intrin.h|\__mm_ucomigt_sd(_m128d,_m128d) \_|
|[_mm_ucomigt_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomigt_ss)|SSE|intrin.h|\__mm_ucomigt_ss(_m128、_m128) \_|
|[_mm_ucomile_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomile_sd)|SSE2|intrin.h|\__mm_ucomile_sd(_m128d、_m128d) \_|
|[_mm_ucomile_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomile_ss)|SSE|intrin.h|\__mm_ucomile_ss(_m128,_m128) \_|
|[_mm_ucomilt_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomilt_sd)|SSE2|intrin.h|\__mm_ucomilt_sd(_m128d,_m128d) \_|
|[_mm_ucomilt_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomilt_ss)|SSE|intrin.h|\__mm_ucomilt_ss(_m128、_m128) \_|
|[_mm_ucomineq_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomineq_sd)|SSE2|intrin.h|\__mm_ucomineq_sd(_m128d,_m128d) \_|
|[_mm_ucomineq_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomineq_ss)|SSE|intrin.h|\__mm_ucomineq_ss(_m128,_m128) \_|
|[_mm_unpackhi_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpackhi_epi16)|SSE2|intrin.h|__m128i_mm_unpackhi_epi16(_m128i、_m128i)\_ \_|
|[_mm_unpackhi_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpackhi_epi32)|SSE2|intrin.h|__m128i_mm_unpackhi_epi32(_m128i、_m128i)\_ \_|
|[_mm_unpackhi_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpackhi_epi64)|SSE2|intrin.h|__m128i_mm_unpackhi_epi64(_m128i、_m128i)\_ \_|
|[_mm_unpackhi_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpackhi_epi8)|SSE2|intrin.h|__m128i_mm_unpackhi_epi8(_m128i,_m128i)\_ \_|
|[_mm_unpackhi_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpackhi_pd)|SSE2|intrin.h|__m128d_mm_unpackhi_pd(_m128d、_m128d)\_ \_|
|[_mm_unpackhi_pi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpackhi_pi8)|MMX|mmintrin.h|__m64_mm_unpackhi_pi8(__m64、__m64) [3]|
|[_mm_unpackhi_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpackhi_pi16)|MMX|mmintrin.h|__m64_mm_unpackhi_pi16(__m64、__m64) [3]|
|[_mm_unpackhi_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpackhi_pi32)|MMX|mmintrin.h|__m64_mm_unpackhi_pi32(__m64、__m64) [3]|
|[_mm_unpackhi_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpackhi_ps)|SSE|intrin.h|__m128_mm_unpackhi_ps(_m128、_m128)\_ \_|
|[_mm_unpacklo_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpacklo_epi16)|SSE2|intrin.h|__m128i_mm_unpacklo_epi16(_m128i、_m128i)\_ \_|
|[_mm_unpacklo_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpacklo_epi32)|SSE2|intrin.h|__m128i_mm_unpacklo_epi32(_m128i、_m128i)\_ \_|
|[_mm_unpacklo_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpacklo_epi64)|SSE2|intrin.h|__m128i_mm_unpacklo_epi64(_m128i、_m128i)\_ \_|
|[_mm_unpacklo_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpacklo_epi8)|SSE2|intrin.h|__m128i_mm_unpacklo_epi8(_m128i、_m128i)\_ \_|
|[_mm_unpacklo_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpacklo_pd)|SSE2|intrin.h|__m128d_mm_unpacklo_pd(_m128d、_m128d)\_ \_|
|[_mm_unpacklo_pi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpacklo_pi8)|MMX|mmintrin.h|__m64_mm_unpacklo_pi8(__m64、__m64) [3]|
|[_mm_unpacklo_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpacklo_pi16)|MMX|mmintrin.h|__m64_mm_unpacklo_pi16(__m64、__m64) [3]|
|[_mm_unpacklo_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpacklo_pi32)|MMX|mmintrin.h|__m64_mm_unpacklo_pi32(__m64、__m64) [3]|
|[_mm_unpacklo_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpacklo_ps)|SSE|intrin.h|__m128_mm_unpacklo_ps(_m128、_m128)\_ \_|
|[_mm_xor_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_xor_pd)|SSE2|intrin.h|__m128d_mm_xor_pd(_m128d、_m128d)\_ \_|
|[_mm_xor_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_xor_ps)|SSE|intrin.h|__m128_mm_xor_ps(_m128、_m128)\_ \_|
|[_mm_xor_si64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_xor_si64)|MMX|mmintrin.h|__m64_mm_xor_si64(_m64、_m64)\_ \_[3]|
|[_mm_xor_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_xor_si128)|SSE2|intrin.h|__m128i_mm_xor_si128(_m128i、_m128i)\_ \_|
|[_mm256_abs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_abs_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_abs_epi16(_m256i)\_|
|[_mm256_abs_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_abs_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_abs_epi32(_m256i)\_|
|[_mm256_abs_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_abs_epi8)|AVX2 [2]|immintrin.h|__m256i_mm256_abs_epi8(_m256i)\_|
|[_mm256_add_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_add_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_add_epi16(_m256i、_m256i)\_ \_|
|[_mm256_add_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_add_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_add_epi32(_m256i、_m256i)\_ \_|
|[_mm256_add_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_add_epi64)|AVX2 [2]|immintrin.h|__m256i_mm256_add_epi64(_m256i、_m256i)\_ \_|
|[_mm256_add_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_add_epi8)|AVX2 [2]|immintrin.h|__m256i_mm256_add_epi8(_m256i、_m256i)\_ \_|
|[_mm256_add_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_add_pd)|AVX [2]|immintrin.h|__m256d_mm256_add_pd(_m256d、_m256d)\_ \_|
|[_mm256_add_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_add_ps)|AVX [2]|immintrin.h|__m256_mm256_add_ps(_m256、_m256)\_ \_|
|[_mm256_adds_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_adds_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_adds_epi16(_m256i、_m256i)\_ \_|
|[_mm256_adds_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_adds_epi8)|AVX2 [2]|immintrin.h|__m256i_mm256_adds_epi8(_m256i、_m256i)\_ \_|
|[_mm256_adds_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_adds_epu16)|AVX2 [2]|immintrin.h|__m256i_mm256_adds_epu16(_m256i、_m256i)\_ \_|
|[_mm256_adds_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_adds_epu8)|AVX2 [2]|immintrin.h|__m256i_mm256_adds_epu8(_m256i、_m256i)\_ \_|
|[_mm256_addsub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_addsub_pd)|AVX [2]|immintrin.h|__m256d_mm256_addsub_pd(_m256d、_m256d)\_ \_|
|[_mm256_addsub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_addsub_ps)|AVX [2]|immintrin.h|__m256_mm256_addsub_ps(_m256、_m256)\_ \_|
|[_mm256_alignr_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_alignr_epi8)|AVX2 [2]|immintrin.h|__m256i_mm256_alignr_epi8(_m256i、_m256i、\_\_康斯特)|
|[_mm256_and_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_and_pd)|AVX [2]|immintrin.h|__m256d_mm256_and_pd(_m256d、_m256d)\_ \_|
|[_mm256_and_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_and_ps)|AVX [2]|immintrin.h|__m256_mm256_and_ps(_m256、_m256)\_ \_|
|[_mm256_and_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_and_si256)|AVX2 [2]|immintrin.h|__m256i_mm256_and_si256(_m256i、_m256i)\_ \_|
|[_mm256_andnot_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_andnot_pd)|AVX [2]|immintrin.h|__m256d_mm256_andnot_pd(_m256d、_m256d)\_ \_|
|[_mm256_andnot_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_andnot_ps)|AVX [2]|immintrin.h|__m256_mm256_andnot_ps(_m256,_m256)\_ \_|
|[_mm256_andnot_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_andnot_si256)|AVX2 [2]|immintrin.h|__m256i_mm256_andnot_si256(_m256i、_m256i)\_ \_|
|[_mm256_avg_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_avg_epu16)|AVX2 [2]|immintrin.h|__m256i_mm256_avg_epu16(_m256i、_m256i)\_ \_|
|[_mm256_avg_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_avg_epu8)|AVX2 [2]|immintrin.h|__m256i_mm256_avg_epu8(_m256i、_m256i)\_ \_|
|[_mm256_blend_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_blend_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_blend_epi16(_m256i、_m256i、\_\_康斯特)|
|[_mm256_blend_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_blend_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_blend_epi32(_m256i、_m256i、\_\_康斯特)|
|[_mm256_blend_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_blend_pd)|AVX [2]|immintrin.h|__m256d_mm256_blend_pd(_m256d、_m256d、\_\_康斯特)|
|[_mm256_blend_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_blend_ps)|AVX [2]|immintrin.h|__m256_mm256_blend_ps(_m256、_m256、\_\_康斯特)|
|[_mm256_blendv_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_blendv_epi8)|AVX2 [2]|immintrin.h|__m256i_mm256_blendv_epi8(_m256i、_m256i、_m256i)\_ \_ \_|
|[_mm256_blendv_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_blendv_pd)|AVX [2]|immintrin.h|__m256d_mm256_blendv_pd(_m256d、_m256d、_m256d)\_ \_ \_|
|[_mm256_blendv_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_blendv_ps)|AVX [2]|immintrin.h|__m256_mm256_blendv_ps(_m256、_m256、_m256)\_ \_ \_|
|[_mm256_broadcast_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcast_pd)|AVX [2]|immintrin.h|__m256d_mm256_broadcast_pd(_m128d\_康\*斯特 )|
|[_mm256_broadcast_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcast_ps)|AVX [2]|immintrin.h|__m256_mm256_broadcast_ps(_m128\_康\*斯特 )|
|[_mm256_broadcast_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcast_sd)|AVX [2]|immintrin.h|__m256d_mm256_broadcast_sd(雙錐\*)|
|[_mm256_broadcast_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcast_ss)|AVX [2]|immintrin.h|__m256_mm256_broadcast_ss(浮動康斯特\*)|
|[_mm256_broadcastb_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcastb_epi8)|AVX2 [2]|immintrin.h|__m256i_mm256_broadcastb_epi8(_m128i)\_|
|[_mm256_broadcastd_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcastd_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_broadcastd_epi32(_m128i)\_|
|[_mm256_broadcastq_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcastq_epi64)|AVX2 [2]|immintrin.h|__m256i_mm256_broadcastq_epi64(_m128i)\_|
|[_mm256_broadcastsd_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcastsd_pd)|AVX2 [2]|immintrin.h|__m256d_mm256_broadcastsd_pd(_m128d)\_|
|[_mm256_broadcastsi128_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcastsi128_si256)|AVX2 [2]|immintrin.h|__m256i_mm256_broadcastsi128_si256(_m128i)\_|
|[_mm256_broadcastss_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcastss_ps)|AVX2 [2]|immintrin.h|__m256_mm256_broadcastss_ps(_m128)\_|
|[_mm256_broadcastw_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcastw_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_broadcastw_epi16(_m128i)\_|
|[_mm256_castpd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castpd_ps)|AVX [2]|immintrin.h|__m256_mm256_castpd_ps(_m256d)\_|
|[_mm256_castpd_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castpd_si256)|AVX [2]|immintrin.h|__m256i_mm256_castpd_si256(_m256d)\_|
|[_mm256_castpd128_pd256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castpd128_pd256)|AVX [2]|immintrin.h|__m256d_mm256_castpd128_pd256(_m128d)\_|
|[_mm256_castpd256_pd128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castpd256_pd128)|AVX [2]|immintrin.h|__m128d_mm256_castpd256_pd128(_m256d)\_|
|[_mm256_castps_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castps_pd)|AVX [2]|immintrin.h|__m256d_mm256_castps_pd(_m256)\_|
|[_mm256_castps_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castps_si256)|AVX [2]|immintrin.h|__m256i_mm256_castps_si256(_m256)\_|
|[_mm256_castps128_ps256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castps128_ps256)|AVX [2]|immintrin.h|__m256_mm256_castps128_ps256(_m128)\_|
|[_mm256_castps256_ps128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castps256_ps128)|AVX [2]|immintrin.h|__m128_mm256_castps256_ps128(_m256)\_|
|[_mm256_castsi128_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castsi128_si256)|AVX [2]|immintrin.h|__m256i_mm256_castsi128_si256(_m128i)\_|
|[_mm256_castsi256_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castsi256_pd)|AVX [2]|immintrin.h|__m256d_mm256_castsi256_pd(_m256i)\_|
|[_mm256_castsi256_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castsi256_ps)|AVX [2]|immintrin.h|__m256_mm256_castsi256_ps(_m256i)\_|
|[_mm256_castsi256_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castsi256_si128)|AVX [2]|immintrin.h|__m128i_mm256_castsi256_si128(_m256i)\_|
|_mm256_cmov_si256|XOP [1]|ammintrin.h|__m256i_mm256_cmov_si256(_m256i、_m256i、_m256i)\_ \_ \_|
|[_mm256_cmp_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cmp_pd)|AVX [2]|immintrin.h|__m256d_mm256_cmp_pd(_m256d、_m256d、\_\_康斯特)|
|[_mm256_cmp_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cmp_ps)|AVX [2]|immintrin.h|__m256_mm256_cmp_ps(_m256、_m256、\_\_康斯特)|
|[_mm256_cmpeq_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cmpeq_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_cmpeq_epi16(_m256i、_m256i)\_ \_|
|[_mm256_cmpeq_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cmpeq_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_cmpeq_epi32(_m256i、_m256i)\_ \_|
|[_mm256_cmpeq_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cmpeq_epi64)|AVX2 [2]|immintrin.h|__m256i_mm256_cmpeq_epi64(_m256i、_m256i)\_ \_|
|[_mm256_cmpeq_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cmpeq_epi8)|AVX2 [2]|immintrin.h|__m256i_mm256_cmpeq_epi8(_m256i、_m256i)\_ \_|
|[_mm256_cmpgt_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cmpgt_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_cmpgt_epi16(_m256i、_m256i)\_ \_|
|[_mm256_cmpgt_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cmpgt_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_cmpgt_epi32(_m256i、_m256i)\_ \_|
|[_mm256_cmpgt_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cmpgt_epi64)|AVX2 [2]|immintrin.h|__m256i_mm256_cmpgt_epi64(_m256i、_m256i)\_ \_|
|[_mm256_cmpgt_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cmpgt_epi8)|AVX2 [2]|immintrin.h|__m256i_mm256_cmpgt_epi8(_m256i、_m256i)\_ \_|
|[_mm256_cvtepi16_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepi16_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_cvtepi16_epi32(_m128i)\_|
|[_mm256_cvtepi16_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepi16_epi64)|AVX2 [2]|immintrin.h|__m256i_mm256_cvtepi16_epi64(_m128i)\_|
|[_mm256_cvtepi32_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepi32_epi64)|AVX2 [2]|immintrin.h|__m256i_mm256_cvtepi32_epi64(_m128i)\_|
|[_mm256_cvtepi32_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepi32_pd)|AVX [2]|immintrin.h|__m256d_mm256_cvtepi32_pd(_m128i)\_|
|[_mm256_cvtepi32_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepi32_ps)|AVX [2]|immintrin.h|__m256_mm256_cvtepi32_ps(_m256i)\_|
|[_mm256_cvtepi8_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepi8_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_cvtepi8_epi16(_m128i)\_|
|[_mm256_cvtepi8_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepi8_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_cvtepi8_epi32(_m128i)\_|
|[_mm256_cvtepi8_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepi8_epi64)|AVX2 [2]|immintrin.h|__m256i_mm256_cvtepi8_epi64(_m128i)\_|
|[_mm256_cvtepu16_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepu16_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_cvtepu16_epi32(_m128i)\_|
|[_mm256_cvtepu16_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepu16_epi64)|AVX2 [2]|immintrin.h|__m256i_mm256_cvtepu16_epi64(_m128i)\_|
|[_mm256_cvtepu32_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepu32_epi64)|AVX2 [2]|immintrin.h|__m256i_mm256_cvtepu32_epi64(_m128i)\_|
|[_mm256_cvtepu8_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepu8_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_cvtepu8_epi16(_m128i)\_|
|[_mm256_cvtepu8_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepu8_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_cvtepu8_epi32 (_m128i)\_|
|[_mm256_cvtepu8_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepu8_epi64)|AVX2 [2]|immintrin.h|__m256i_mm256_cvtepu8_epi64(_m128i)\_|
|[_mm256_cvtpd_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtpd_epi32)|AVX [2]|immintrin.h|__m128i_mm256_cvtpd_epi32(_m256d)\_|
|[_mm256_cvtpd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtpd_ps)|AVX [2]|immintrin.h|__m128_mm256_cvtpd_ps(_m256d)\_|
|[_mm256_cvtph_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtph_ps)|F16C [2]|immintrin.h|__m256_mm256_cvtph_ps(_m128i)\_|
|[_mm256_cvtps_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtps_epi32)|AVX [2]|immintrin.h|__m256i_mm256_cvtps_epi32(_m256)\_|
|[_mm256_cvtps_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtps_pd)|AVX [2]|immintrin.h|__m256d_mm256_cvtps_pd(_m128)\_|
|[_mm256_cvtps_ph](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtps_ph)|F16C [2]|immintrin.h|__m128i_mm256_cvtps_ph(_m256,\_康斯特)|
|[_mm256_cvttpd_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvttpd_epi32)|AVX [2]|immintrin.h|__m128i_mm256_cvttpd_epi32(_m256d)\_|
|[_mm256_cvttps_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvttps_epi32)|AVX [2]|immintrin.h|__m256i_mm256_cvttps_epi32(_m256)\_|
|[_mm256_div_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_div_pd)|AVX [2]|immintrin.h|__m256d_mm256_div_pd(_m256d、_m256d)\_ \_|
|[_mm256_div_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_div_ps)|AVX [2]|immintrin.h|__m256_mm256_div_ps(_m256、_m256)\_ \_|
|[_mm256_dp_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_dp_ps)|AVX [2]|immintrin.h|__m256_mm256_dp_ps(_m256、_m256、\_\_康斯特)|
|[_mm256_extractf128_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_extractf128_pd)|AVX [2]|immintrin.h|__m128d_mm256_extractf128_pd(_m256d,\_康斯特)|
|[_mm256_extractf128_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_extractf128_ps)|AVX [2]|immintrin.h|__m128_mm256_extractf128_ps(_m256,\_康斯特)|
|[_mm256_extractf128_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_extractf128_si256)|AVX [2]|immintrin.h|__m128i_mm256_extractf128_si256(_m256i,\_康斯特)|
|[_mm256_extracti128_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_extracti128_si256)|AVX2 [2]|immintrin.h|__m128i_mm256_extracti128_si256(_m256i\_|
|[_mm256_fmadd_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fmadd_pd)|FMA [2]|immintrin.h|__m256d_mm256_fmadd_pd(_m256d、_m256d、_m256d)\_ \_ \_|
|[_mm256_fmadd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fmadd_ps)|FMA [2]|immintrin.h|__m256_mm256_fmadd_ps(_m256、_m256、_m256)\_ \_ \_|
|[_mm256_fmaddsub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fmaddsub_pd)|FMA [2]|immintrin.h|__m256d_mm256_fmaddsub_pd(_m256d、_m256d、_m256d)\_ \_ \_|
|[_mm256_fmaddsub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fmaddsub_ps)|FMA [2]|immintrin.h|__m256_mm256_fmaddsub_ps(_m256、_m256、_m256)\_ \_ \_|
|[_mm256_fmsub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fmsub_pd)|FMA [2]|immintrin.h|__m256d_mm256_fmsub_pd(_m256d、_m256d、_m256d)\_ \_ \_|
|[_mm256_fmsub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fmsub_ps)|FMA [2]|immintrin.h|__m256_mm256_fmsub_ps(_m256、_m256、_m256)\_ \_ \_|
|[_mm256_fmsubadd_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fmsubadd_pd)|FMA [2]|immintrin.h|__m256d_mm256_fmsubadd_pd(_m256d、_m256d、_m256d)\_ \_ \_|
|[_mm256_fmsubadd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fmsubadd_ps)|FMA [2]|immintrin.h|__m256_mm256_fmsubadd_ps(_m256、_m256、_m256)\_ \_ \_|
|[_mm256_fnmadd_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fnmadd_pd)|FMA [2]|immintrin.h|__m256d_mm256_fnmadd_pd(_m256d、_m256d、_m256d)\_ \_ \_|
|[_mm256_fnmadd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fnmadd_ps)|FMA [2]|immintrin.h|__m256_mm256_fnmadd_ps(_m256、_m256、_m256)\_ \_ \_|
|[_mm256_fnmsub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fnmsub_pd)|FMA [2]|immintrin.h|__m256d_mm256_fnmsub_pd(_m256d、_m256d、_m256d)\_ \_ \_|
|[_mm256_fnmsub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fnmsub_ps)|FMA [2]|immintrin.h|__m256_mm256_fnmsub_ps(_m256、_m256、_m256)\_ \_ \_|
|_mm256_frcz_pd|XOP [1]|ammintrin.h|__m256d_mm256_frcz_pd(_m256d)\_|
|_mm256_frcz_ps|XOP [1]|ammintrin.h|__m256_mm256_frcz_ps(_m256)\_|
|[_mm256_hadd_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_hadd_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_hadd_epi16(_m256i、_m256i)\_ \_|
|[_mm256_hadd_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_hadd_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_hadd_epi32(_m256i,_m256i)\_ \_|
|[_mm256_hadd_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_hadd_pd)|AVX [2]|immintrin.h|__m256d_mm256_hadd_pd(_m256d、_m256d)\_ \_|
|[_mm256_hadd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_hadd_ps)|AVX [2]|immintrin.h|__m256_mm256_hadd_ps(_m256、_m256)\_ \_|
|[_mm256_hadds_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_hadds_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_hadds_epi16(_m256i、_m256i)\_ \_|
|[_mm256_hsub_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_hsub_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_hsub_epi16(_m256i、_m256i)\_ \_|
|[_mm256_hsub_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_hsub_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_hsub_epi32(_m256i、_m256i)\_ \_|
|[_mm256_hsub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_hsub_pd)|AVX [2]|immintrin.h|__m256d_mm256_hsub_pd(_m256d、_m256d)\_ \_|
|[_mm256_hsub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_hsub_ps)|AVX [2]|immintrin.h|__m256_mm256_hsub_ps(_m256、_m256)\_ \_|
|[_mm256_hsubs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_hsubs_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_hsubs_epi16(_m256i、_m256i)\_ \_|
|[_mm256_i32gather_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_i32gather_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_i32gather_epi32(int const, \* \__m256i, const int)|
|[_mm256_i32gather_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_i32gather_epi64)|AVX2 [2]|immintrin.h|__m256i_mm256_i32gather_epi64(_int64\_康\*斯特 ,_m128i,\_康斯特)|
|[_mm256_i32gather_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_i32gather_pd)|AVX2 [2]|immintrin.h|__m256d_mm256_i32gather_pd(雙錐\*,_m128i,\_康斯特)|
|[_mm256_i32gather_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_i32gather_ps)|AVX2 [2]|immintrin.h|__m256_mm256_i32gather_ps(浮式康\*\_斯特 ,_m256i,const int)|
|[_mm256_i64gather_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_i64gather_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_i64gather_epi32(int const,_m256i,const \* \_int)|
|[_mm256_i64gather_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_i64gather_epi64)|AVX2 [2]|immintrin.h|__m256i_mm256_i64gather_epi64(_int64\_康\*斯特 ,_m256i,\_康斯特)|
|[_mm256_i64gather_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_i64gather_pd)|AVX2 [2]|immintrin.h|__m256d_mm256_i64gather_pd(雙錐\*體、_m256i、\_康斯特)|
|[_mm256_i64gather_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_i64gather_ps)|AVX2 [2]|immintrin.h|__m128_mm256_i64gather_ps(浮式康\*\_斯特 、_m256i、康斯特)|
|[_mm256_insertf128_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_insertf128_pd)|AVX [2]|immintrin.h|__m256d_mm256_insertf128_pd(_m256d、_m128d、\_\_內)|
|[_mm256_insertf128_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_insertf128_ps)|AVX [2]|immintrin.h|__m256_mm256_insertf128_ps(_m256、_m128、\_\_國際)|
|[_mm256_insertf128_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_insertf128_si256)|AVX [2]|immintrin.h|__m256i_mm256_insertf128_si256(_m256i、_m128i、\_\_國際)|
|[_mm256_inserti128_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_inserti128_si256)|AVX2 [2]|immintrin.h|__m256i_mm256_inserti128_si256(_m256i、_m128i、\_\_內)|
|[_mm256_lddqu_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_lddqu_si256)|AVX [2]|immintrin.h|__m256i_mm256_lddqu_si256(\_ \*_m256i )|
|[_mm256_load_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_load_pd)|AVX [2]|immintrin.h|__m256d_mm256_load_pd(雙錐\*)|
|[_mm256_load_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_load_ps)|AVX [2]|immintrin.h|__m256_mm256_load_ps(浮式康\*斯特)|
|[_mm256_load_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_load_si256)|AVX [2]|immintrin.h|__m256i_mm256_load_si256(\_ \*_m256i )|
|[_mm256_loadu_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_loadu_pd)|AVX [2]|immintrin.h|__m256d_mm256_loadu_pd(雙錐\*)|
|[_mm256_loadu_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_loadu_ps)|AVX [2]|immintrin.h|__m256_mm256_loadu_ps(浮動康斯特\*)|
|[_mm256_loadu_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_loadu_si256)|AVX [2]|immintrin.h|__m256i_mm256_loadu_si256(\_ \*_m256i )|
|_mm256_macc_pd|FMA4 [1]|ammintrin.h|__m256d_mm_macc_pd(_m256d、_m256d、_m256d)\_ \_ \_|
|_mm256_macc_ps|FMA4 [1]|ammintrin.h|__m256_mm_macc_ps(_m256、_m256、_m256)\_ \_ \_|
|[_mm256_madd_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_madd_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_madd_epi16(_m256i、_m256i)\_ \_|
|_mm256_maddsub_pd|FMA4 [1]|ammintrin.h|__m256d_mm_maddsub_pd(_m256d、_m256d、_m256d)\_ \_ \_|
|_mm256_maddsub_ps|FMA4 [1]|ammintrin.h|__m256_mm_maddsub_ps(_m256、_m256、_m256)\_ \_ \_|
|[_mm256_maddubs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_maddubs_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_maddubs_epi16(_m256i、_m256i)\_ \_|
|[_mm256_mask_i32gather_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mask_i32gather_epi32)|AVX2 [2]|immintrin.h|\*__m256i_mm256_mask_i32gather_epi32(_m256i、_m256i、_m256i、_m256i、\_\_\_康斯特)|
|[_mm256_mask_i32gather_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mask_i32gather_epi64)|AVX2 [2]|immintrin.h|\*__m256i_mm256_mask_i32gather_epi64(_m256i、_int64、_m128i、_m256i、\_\_\_\_康斯特)|
|[_mm256_mask_i32gather_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mask_i32gather_pd)|AVX2 [2]|immintrin.h|__m256d_mm256_mask_i32gather_pd(_m256d、\_雙\*錐 、_m128i、_m256d、\_\_康斯特)|
|[_mm256_mask_i32gather_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mask_i32gather_ps)|AVX2 [2]|immintrin.h|__m256_mm256_mask_i32gather_ps(_m256、\_浮\*式 、_m256i、_m256、\_\_康斯特)|
|[_mm256_mask_i64gather_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mask_i64gather_epi32)|AVX2 [2]|immintrin.h|\*__m128i_mm256_mask_i64gather_epi32(_m128i、_m256i、_m128i、\_\_\_康斯特)|
|[_mm256_mask_i64gather_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mask_i64gather_epi64)|AVX2 [2]|immintrin.h|\*__m256i_mm256_mask_i64gather_epi64(_m256i、_int64、_m256i、_m256i、\_\_\_\_康斯特)|
|[_mm256_mask_i64gather_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mask_i64gather_pd)|AVX2 [2]|immintrin.h|__m256d_mm256_mask_i64gather_pd(_m256d、\_雙\*錐 、_m256i、_m256d、\_\_康斯特)|
|[_mm256_mask_i64gather_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mask_i64gather_ps)|AVX2 [2]|immintrin.h|__m128_mm256_mask_i64gather_ps(_m128、\_浮\*點 、_m256i、_m128、\_\_康斯特)|
|[_mm256_maskload_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_maskload_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_maskload_epi32(_m256i) \* \_|
|[_mm256_maskload_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_maskload_epi64)|AVX2 [2]|immintrin.h|__m256i_mm256_maskload_epi64(_int64\_康\*斯特 ,_m256i) \_|
|[_mm256_maskload_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_maskload_pd)|AVX [2]|immintrin.h|__m256d_mm256_maskload_pd(雙錐\*,_m256i) \_|
|[_mm256_maskload_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_maskload_ps)|AVX [2]|immintrin.h|__m256_mm256_maskload_ps(浮式康\*\_斯特 ,_m256i)|
|[_mm256_maskstore_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_maskstore_epi32)|AVX2 [2]|immintrin.h|空_mm256_maskstore_epi32(國際\*,_m256i,_m256i) \_ \_|
|[_mm256_maskstore_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_maskstore_epi64)|AVX2 [2]|immintrin.h|空_mm256_maskstore_epi64(_int64、_m256i、_m256i)\_ \* \_ \_|
|[_mm256_maskstore_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_maskstore_pd)|AVX [2]|immintrin.h|空_mm256_maskstore_pd(雙\*,_m256i,_m256d) \_ \_|
|[_mm256_maskstore_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_maskstore_ps)|AVX [2]|immintrin.h|空_mm256_maskstore_ps(浮\*子\_、_m256i、_m256) \_|
|[_mm256_max_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_max_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_max_epi16(_m256i、_m256i)\_ \_|
|[_mm256_max_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_max_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_max_epi32(_m256i、_m256i)\_ \_|
|[_mm256_max_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_max_epi8)|AVX2 [2]|immintrin.h|__m256i_mm256_max_epi8(_m256i、_m256i)\_ \_|
|[_mm256_max_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_max_epu16)|AVX2 [2]|immintrin.h|__m256i_mm256_max_epu16(_m256i、_m256i)\_ \_|
|[_mm256_max_epu32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_max_epu32)|AVX2 [2]|immintrin.h|__m256i_mm256_max_epu32(_m256i、_m256i)\_ \_|
|[_mm256_max_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_max_epu8)|AVX2 [2]|immintrin.h|__m256i_mm256_max_epu8(_m256i、_m256i)\_ \_|
|[_mm256_max_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_max_pd)|AVX [2]|immintrin.h|__m256d_mm256_max_pd(_m256d、_m256d)\_ \_|
|[_mm256_max_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_max_ps)|AVX [2]|immintrin.h|__m256_mm256_max_ps(_m256、_m256)\_ \_|
|[_mm256_min_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_min_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_min_epi16(_m256i、_m256i)\_ \_|
|[_mm256_min_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_min_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_min_epi32(_m256i、_m256i)\_ \_|
|[_mm256_min_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_min_epi8)|AVX2 [2]|immintrin.h|__m256i_mm256_min_epi8(_m256i、_m256i)\_ \_|
|[_mm256_min_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_min_epu16)|AVX2 [2]|immintrin.h|__m256i_mm256_min_epu16(_m256i、_m256i)\_ \_|
|[_mm256_min_epu32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_min_epu32)|AVX2 [2]|immintrin.h|__m256i_mm256_min_epu32(_m256i、_m256i)\_ \_|
|[_mm256_min_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_min_epu8)|AVX2 [2]|immintrin.h|__m256i_mm256_min_epu8(_m256i、_m256i)\_ \_|
|[_mm256_min_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_min_pd)|AVX [2]|immintrin.h|__m256d_mm256_min_pd(_m256d、_m256d)\_ \_|
|[_mm256_min_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_min_ps)|AVX [2]|immintrin.h|__m256_mm256_min_ps(_m256、_m256)\_ \_|
|[_mm256_movedup_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_movedup_pd)|AVX [2]|immintrin.h|__m256d_mm256_movedup_pd(_m256d)\_|
|[_mm256_movehdup_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_movehdup_ps)|AVX [2]|immintrin.h|__m256_mm256_movehdup_ps(_m256)\_|
|[_mm256_moveldup_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_moveldup_ps)|AVX [2]|immintrin.h|__m256_mm256_moveldup_ps(_m256)\_|
|[_mm256_movemask_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_movemask_epi8)|AVX2 [2]|immintrin.h|_mm256_movemask_epi8(_m256i)\_|
|[_mm256_movemask_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_movemask_pd)|AVX [2]|immintrin.h|_mm256_movemask_pd(_m256d)\_|
|[_mm256_movemask_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_movemask_ps)|AVX [2]|immintrin.h|_mm256_movemask_ps(_m256)\_|
|[_mm256_mpsadbw_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mpsadbw_epu8)|AVX2 [2]|immintrin.h|__m256i_mm256_mpsadbw_epu8(_m256i、_m256i、\_\_康斯特)|
|_mm256_msub_pd|FMA4 [1]|ammintrin.h|__m256d_mm_msub_pd(_m256d、_m256d、_m256d)\_ \_ \_|
|_mm256_msub_ps|FMA4 [1]|ammintrin.h|__m256_mm_msub_ps(_m256、_m256、_m256)\_ \_ \_|
|_mm256_msubadd_pd|FMA4 [1]|ammintrin.h|__m256d_mm_msubadd_pd(_m256d、_m256d、_m256d)\_ \_ \_|
|_mm256_msubadd_ps|FMA4 [1]|ammintrin.h|__m256_mm_msubadd_ps(_m256、_m256、_m256)\_ \_ \_|
|[_mm256_mul_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mul_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_mul_epi32(_m256i、_m256i)\_ \_|
|[_mm256_mul_epu32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mul_epu32)|AVX2 [2]|immintrin.h|__m256i_mm256_mul_epu32(_m256i、_m256i)\_ \_|
|[_mm256_mul_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mul_pd)|AVX [2]|immintrin.h|__m256d_mm256_mul_pd(_m256d、_m256d)\_ \_|
|[_mm256_mul_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mul_ps)|AVX [2]|immintrin.h|__m256_mm256_mul_ps(_m256、_m256)\_ \_|
|[_mm256_mulhi_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mulhi_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_mulhi_epi16(_m256i、_m256i)\_ \_|
|[_mm256_mulhi_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mulhi_epu16)|AVX2 [2]|immintrin.h|__m256i_mm256_mulhi_epu16(_m256i,_m256i)\_ \_|
|[_mm256_mulhrs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mulhrs_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_mulhrs_epi16(_m256i、_m256i)\_ \_|
|[_mm256_mullo_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mullo_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_mullo_epi16(_m256i、_m256i)\_ \_|
|[_mm256_mullo_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mullo_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_mullo_epi32(_m256i、_m256i)\_ \_|
|_mm256_nmacc_pd|FMA4 [1]|ammintrin.h|__m256d_mm_nmacc_pd(_m256d、_m256d、_m256d)\_ \_ \_|
|_mm256_nmacc_ps|FMA4 [1]|ammintrin.h|__m256_mm_nmacc_ps(_m256、_m256、_m256)\_ \_ \_|
|_mm256_nmsub_pd|FMA4 [1]|ammintrin.h|__m256d_mm_nmsub_pd(_m256d、_m256d、_m256d)\_ \_ \_|
|_mm256_nmsub_ps|FMA4 [1]|ammintrin.h|__m256_mm_nmsub_ps(_m256、_m256、_m256)\_ \_ \_|
|[_mm256_or_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_or_pd)|AVX [2]|immintrin.h|__m256d_mm256_or_pd(_m256d、_m256d)\_ \_|
|[_mm256_or_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_or_ps)|AVX [2]|immintrin.h|__m256_mm256_or_ps(_m256、_m256)\_ \_|
|[_mm256_or_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_or_si256)|AVX2 [2]|immintrin.h|__m256i_mm256_or_si256(_m256i、_m256i)\_ \_|
|[_mm256_packs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_packs_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_packs_epi16(_m256i、_m256i)\_ \_|
|[_mm256_packs_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_packs_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_packs_epi32(_m256i、_m256i)\_ \_|
|[_mm256_packus_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_packus_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_packus_epi16(_m256i,_m256i)\_ \_|
|[_mm256_packus_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_packus_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_packus_epi32(_m256i、_m256i)\_ \_|
|[_mm256_permute_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permute_pd)|AVX [2]|immintrin.h|__m256d_mm256_permute_pd(_m256d,int)\_|
|[_mm256_permute_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permute_ps)|AVX [2]|immintrin.h|__m256_mm256_permute_ps(_m256,int)\_|
|_mm256_permute2_pd|XOP [1]|ammintrin.h|__m256d_mm256_permute2_pd(_m256d、_m256d、_m256i、\_\_\_內)|
|_mm256_permute2_ps|XOP [1]|ammintrin.h|__m256_mm256_permute2_ps(_m256、_m256、_m256i、\_\_\_國際)|
|[_mm256_permute2f128_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permute2f128_pd)|AVX [2]|immintrin.h|__m256d_mm256_permute2f128_pd(_m256d、_m256d、\_\_國際)|
|[_mm256_permute2f128_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permute2f128_ps)|AVX [2]|immintrin.h|__m256_mm256_permute2f128_ps(_m256、_m256、\_\_國際)|
|[_mm256_permute2f128_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permute2f128_si256)|AVX [2]|immintrin.h|__m256i_mm256_permute2f128_si256(_m256i、_m256i、\_\_國際)|
|[_mm256_permute2x128_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permute2x128_si256)|AVX2 [2]|immintrin.h|__m256i_mm256_permute2x128_si256(_m256i、_m256i、\_\_康斯特)|
|[_mm256_permute4x64_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permute4x64_epi64)|AVX2 [2]|immintrin.h|__m256i_mm256_permute4x64_epi64(_m256i,\_康斯特)|
|[_mm256_permute4x64_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permute4x64_pd)|AVX2 [2]|immintrin.h|__m256d_mm256_permute4x64_pd(_m256d,\_康斯特)|
|[_mm256_permutevar_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permutevar_pd)|AVX [2]|immintrin.h|__m256d_mm256_permutevar_pd(_m256d、_m256i)\_ \_|
|[_mm256_permutevar_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permutevar_ps)|AVX [2]|immintrin.h|__m256_mm256_permutevar_ps(_m256、_m256i)\_ \_|
|[_mm256_permutevar8x32_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permutevar8x32_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_permutevar8x32_epi32(_m256i、_m256i)\_ \_|
|[_mm256_permutevar8x32_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permutevar8x32_ps)|AVX2 [2]|immintrin.h|__m256_mm256_permutevar8x32_ps(_m256、_m256i)\_ \_|
|[_mm256_rcp_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_rcp_ps)|AVX [2]|immintrin.h|__m256_mm256_rcp_ps(_m256)\_|
|[_mm256_round_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_round_pd)|AVX [2]|immintrin.h|__m256d_mm256_round_pd(_m256d,int)\_|
|[_mm256_round_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_round_ps)|AVX [2]|immintrin.h|__m256_mm256_round_ps(_m256\_|
|[_mm256_rsqrt_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_rsqrt_ps)|AVX [2]|immintrin.h|__m256_mm256_rsqrt_ps(_m256)\_|
|[_mm256_sad_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sad_epu8)|AVX2 [2]|immintrin.h|__m256i_mm256_sad_epu8(_m256i、_m256i)\_ \_|
|[_mm256_set_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_set_epi16)|AVX [2]|immintrin.h|(__m256i _mm256_set_epi16(short|
|[_mm256_set_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_set_epi32)|AVX [2]|immintrin.h|__m256i_mm256_set_epi32(int、int、int、int、int、int、int、int、int、int、int)|
|[_mm256_set_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_set_epi8)|AVX [2]|immintrin.h|__m256i _mm256_set_epi8(char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char)|
|[_mm256_set_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_set_pd)|AVX [2]|immintrin.h|__m256d_mm256_set_pd(雙、雙、雙、雙)|
|[_mm256_set_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_set_ps)|AVX [2]|immintrin.h|__m256_mm256_set_ps(浮、浮、浮、浮、浮、浮、浮)|
|[_mm256_set1_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_set1_epi16)|AVX [2]|immintrin.h|__m256i _mm256_set1_epi16(short)|
|[_mm256_set1_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_set1_epi32)|AVX [2]|immintrin.h|__m256i _mm256_set1_epi32(int)|
|[_mm256_set1_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_set1_epi8)|AVX [2]|immintrin.h|__m256i _mm256_set1_epi8(char)|
|[_mm256_set1_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_set1_pd)|AVX [2]|immintrin.h|__m256d _mm256_set1_pd(double)|
|[_mm256_set1_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_set1_ps)|AVX [2]|immintrin.h|__m256 _mm256_set1_ps(float)|
|[_mm256_setr_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_setr_epi16)|AVX [2]|immintrin.h|(__m256i _mm256_setr_epi16(short|
|[_mm256_setr_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_setr_epi32)|AVX [2]|immintrin.h|__m256i_mm256_setr_epi32(int、int、int、int、int、int、int、int、int、int)|
|[_mm256_setr_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_setr_epi8)|AVX [2]|immintrin.h|(__m256i _mm256_setr_epi8(char|
|[_mm256_setr_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_setr_pd)|AVX [2]|immintrin.h|__m256d_mm256_setr_pd(雙、雙、雙、雙)|
|[_mm256_setr_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_setr_ps)|AVX [2]|immintrin.h|__m256_mm256_setr_ps(浮、浮、浮、浮、浮、浮、浮)|
|[_mm256_setzero_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_setzero_pd)|AVX [2]|immintrin.h|__m256d _mm256_setzero_pd(void)|
|[_mm256_setzero_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_setzero_ps)|AVX [2]|immintrin.h|__m256 _mm256_setzero_ps(void)|
|[_mm256_setzero_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_setzero_si256)|AVX [2]|immintrin.h|__m256i _mm256_setzero_si256(void)|
|[_mm256_shuffle_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_shuffle_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_shuffle_epi32(_m256i,\_康斯特)|
|[_mm256_shuffle_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_shuffle_epi8)|AVX2 [2]|immintrin.h|__m256i_mm256_shuffle_epi8(_m256i,_m256i)\_ \_|
|[_mm256_shuffle_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_shuffle_pd)|AVX [2]|immintrin.h|__m256d_mm256_shuffle_pd(_m256d、_m256d、\_\_康斯特)|
|[_mm256_shuffle_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_shuffle_ps)|AVX [2]|immintrin.h|__m256_mm256_shuffle_ps(_m256、_m256、\_\_康斯特)|
|[_mm256_shufflehi_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_shufflehi_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_shufflehi_epi16(_m256i,\_康斯特)|
|[_mm256_shufflelo_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_shufflelo_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_shufflelo_epi16(_m256i,\_康斯特)|
|[_mm256_sign_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sign_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_sign_epi16(_m256i、_m256i)\_ \_|
|[_mm256_sign_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sign_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_sign_epi32(_m256i、_m256i)\_ \_|
|[_mm256_sign_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sign_epi8)|AVX2 [2]|immintrin.h|__m256i_mm256_sign_epi8(_m256i、_m256i)\_ \_|
|[_mm256_sll_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sll_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_sll_epi16(_m256i、_m128i)\_ \_|
|[_mm256_sll_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sll_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_sll_epi32(_m256i、_m128i)\_ \_|
|[_mm256_sll_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sll_epi64)|AVX2 [2]|immintrin.h|__m256i_mm256_sll_epi64(_m256i、_m128i)\_ \_|
|[_mm256_slli_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_slli_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_slli_epi16(_m256i,int)\_|
|[_mm256_slli_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_slli_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_slli_epi32(_m256i,int)\_|
|[_mm256_slli_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_slli_epi64)|AVX2 [2]|immintrin.h|__m256i_mm256_slli_epi64(_m256i\_|
|[_mm256_slli_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_slli_si256)|AVX2 [2]|immintrin.h|__m256i_mm256_slli_si256(_m256i\_|
|[_mm256_sllv_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sllv_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_sllv_epi32(_m256i、_m256i)\_ \_|
|[_mm256_sllv_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sllv_epi64)|AVX2 [2]|immintrin.h|__m256i_mm256_sllv_epi64(_m256i、_m256i)\_ \_|
|[_mm256_sqrt_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sqrt_pd)|AVX [2]|immintrin.h|__m256d_mm256_sqrt_pd(_m256d)\_|
|[_mm256_sqrt_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sqrt_ps)|AVX [2]|immintrin.h|__m256_mm256_sqrt_ps(_m256)\_|
|[_mm256_sra_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sra_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_sra_epi16(_m256i、_m128i)\_ \_|
|[_mm256_sra_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sra_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_sra_epi32(_m256i、_m128i)\_ \_|
|[_mm256_srai_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srai_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_srai_epi16(_m256i\_|
|[_mm256_srai_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srai_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_srai_epi32(_m256i,\_國際)|
|[_mm256_srav_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srav_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_srav_epi32(_m256i、_m256i)\_ \_|
|[_mm256_srl_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srl_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_srl_epi16(_m256i、_m128i)\_ \_|
|[_mm256_srl_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srl_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_srl_epi32(_m256i、_m128i)\_ \_|
|[_mm256_srl_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srl_epi64)|AVX2 [2]|immintrin.h|__m256i_mm256_srl_epi64(_m256i、_m128i)\_ \_|
|[_mm256_srli_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srli_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_srli_epi16(_m256i\_|
|[_mm256_srli_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srli_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_srli_epi32(_m256i\_|
|[_mm256_srli_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srli_epi64)|AVX2 [2]|immintrin.h|__m256i_mm256_srli_epi64(_m256i,int)\_|
|[_mm256_srli_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srli_si256)|AVX2 [2]|immintrin.h|__m256i_mm256_srli_si256(_m256i,\_國際)|
|[_mm256_srlv_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srlv_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_srlv_epi32(_m256i、_m256i)\_ \_|
|[_mm256_srlv_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srlv_epi64)|AVX2 [2]|immintrin.h|__m256i_mm256_srlv_epi64(_m256i、_m256i)\_ \_|
|[_mm256_store_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_store_pd)|AVX [2]|immintrin.h|空_mm256_store_pd(雙\*,_m256d) \_|
|[_mm256_store_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_store_ps)|AVX [2]|immintrin.h|空_mm256_store_ps(浮\*子\_,_m256)|
|[_mm256_store_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_store_si256)|AVX [2]|immintrin.h|空_mm256_store_si256(_m256i、_m256i)\_ \* \_|
|[_mm256_storeu_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_storeu_pd)|AVX [2]|immintrin.h|空_mm256_storeu_pd(雙\*,_m256d) \_|
|[_mm256_storeu_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_storeu_ps)|AVX [2]|immintrin.h|空_mm256_storeu_ps(浮\*子\_,_m256)|
|[_mm256_storeu_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_storeu_si256)|AVX [2]|immintrin.h|無效_mm256_storeu_si256(_m256i,_m256i)\_ \* \_|
|[_mm256_stream_load_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_stream_load_si256)|AVX2 [2]|immintrin.h|__m256i_mm256_stream_load_si256(_m256i)\_ \*|
|[_mm256_stream_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_stream_pd)|AVX [2]|immintrin.h|空__mm256_stream_pd(雙\*,_m256d) \_|
|[_mm256_stream_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_stream_ps)|AVX [2]|immintrin.h|空_mm256_stream_ps(浮\*子\_,_m256)|
|[_mm256_stream_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_stream_si256)|AVX [2]|immintrin.h|無效__mm256_stream_si256(_m256i,_m256i)\_ \* \_|
|[_mm256_sub_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sub_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_sub_epi16(_m256i、_m256i)\_ \_|
|[_mm256_sub_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sub_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_sub_epi32(_m256i、_m256i)\_ \_|
|[_mm256_sub_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sub_epi64)|AVX2 [2]|immintrin.h|__m256i_mm256_sub_epi64(_m256i、_m256i)\_ \_|
|[_mm256_sub_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sub_epi8)|AVX2 [2]|immintrin.h|__m256i_mm256_sub_epi8(_m256i、_m256i)\_ \_|
|[_mm256_sub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sub_pd)|AVX [2]|immintrin.h|__m256d_mm256_sub_pd(_m256d、_m256d)\_ \_|
|[_mm256_sub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sub_ps)|AVX [2]|immintrin.h|__m256_mm256_sub_ps(_m256、_m256)\_ \_|
|[_mm256_subs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_subs_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_subs_epi16(_m256i、_m256i)\_ \_|
|[_mm256_subs_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_subs_epi8)|AVX2 [2]|immintrin.h|__m256i_mm256_subs_epi8(_m256i、_m256i)\_ \_|
|[_mm256_subs_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_subs_epu16)|AVX2 [2]|immintrin.h|__m256i_mm256_subs_epu16(_m256i、_m256i)\_ \_|
|[_mm256_subs_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_subs_epu8)|AVX2 [2]|immintrin.h|__m256i_mm256_subs_epu8(_m256i、_m256i)\_ \_|
|[_mm256_testc_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_testc_pd)|AVX [2]|immintrin.h|\__mm256_testc_pd(_m256d,_m256d) \_|
|[_mm256_testc_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_testc_ps)|AVX [2]|immintrin.h|\__mm256_testc_ps(_m256,_m256) \_|
|[_mm256_testc_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_testc_si256)|AVX [2]|immintrin.h|\__mm256_testc_si256(_m256i,_m256i) \_|
|[_mm256_testnzc_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_testnzc_pd)|AVX [2]|immintrin.h|\__mm256_testnzc_pd(_m256d,_m256d) \_|
|[_mm256_testnzc_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_testnzc_ps)|AVX [2]|immintrin.h|\__mm256_testnzc_ps(_m256、_m256) \_|
|[_mm256_testnzc_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_testnzc_si256)|AVX [2]|immintrin.h|\__mm256_testnzc_si256(_m256i,_m256i) \_|
|[_mm256_testz_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_testz_pd)|AVX [2]|immintrin.h|\__mm256_testz_pd(_m256d,_m256d) \_|
|[_mm256_testz_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_testz_ps)|AVX [2]|immintrin.h|\__mm256_testz_ps(_m256,_m256) \_|
|[_mm256_testz_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_testz_si256)|AVX [2]|immintrin.h|\__mm256_testz_si256(_m256i,_m256i) \_|
|[_mm256_unpackhi_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpackhi_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_unpackhi_epi16(_m256i、_m256i)\_ \_|
|[_mm256_unpackhi_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpackhi_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_unpackhi_epi32(_m256i、_m256i)\_ \_|
|[_mm256_unpackhi_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpackhi_epi64)|AVX2 [2]|immintrin.h|__m256i_mm256_unpackhi_epi64(_m256i、_m256i)\_ \_|
|[_mm256_unpackhi_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpackhi_epi8)|AVX2 [2]|immintrin.h|__m256i_mm256_unpackhi_epi8(_m256i、_m256i)\_ \_|
|[_mm256_unpackhi_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpackhi_pd)|AVX [2]|immintrin.h|__m256d_mm256_unpackhi_pd(_m256d、_m256d)\_ \_|
|[_mm256_unpackhi_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpackhi_ps)|AVX [2]|immintrin.h|__m256_mm256_unpackhi_ps(_m256、_m256)\_ \_|
|[_mm256_unpacklo_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpacklo_epi16)|AVX2 [2]|immintrin.h|__m256i_mm256_unpacklo_epi16(_m256i、_m256i)\_ \_|
|[_mm256_unpacklo_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpacklo_epi32)|AVX2 [2]|immintrin.h|__m256i_mm256_unpacklo_epi32(_m256i、_m256i)\_ \_|
|[_mm256_unpacklo_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpacklo_epi64)|AVX2 [2]|immintrin.h|__m256i_mm256_unpacklo_epi64(_m256i、_m256i)\_ \_|
|[_mm256_unpacklo_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpacklo_epi8)|AVX2 [2]|immintrin.h|__m256i_mm256_unpacklo_epi8(_m256i、_m256i)\_ \_|
|[_mm256_unpacklo_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpacklo_pd)|AVX [2]|immintrin.h|__m256d_mm256_unpacklo_pd(_m256d、_m256d)\_ \_|
|[_mm256_unpacklo_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpacklo_ps)|AVX [2]|immintrin.h|__m256_mm256_unpacklo_ps(_m256、_m256)\_ \_|
|[_mm256_xor_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_xor_pd)|AVX [2]|immintrin.h|__m256d_mm256_xor_pd(_m256d、_m256d)\_ \_|
|[_mm256_xor_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_xor_ps)|AVX [2]|immintrin.h|__m256_mm256_xor_ps(_m256、_m256)\_ \_|
|[_mm256_xor_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_xor_si256)|AVX2 [2]|immintrin.h|__m256i_mm256_xor_si256(_m256i、_m256i)\_ \_|
|[_mm256_zeroall](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_zeroall)|AVX [2]|immintrin.h|void _mm256_zeroall(void)|
|[_mm256_zeroupper](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_zeroupper)|AVX [2]|immintrin.h|void _mm256_zeroupper(void)|
|[__movsb](movsb.md)||intrin.h|不合法__movsb(無符號字\*元,未簽署的字\*元,size_t)|
|[__movsd](movsd.md)||intrin.h|空__movsd(無符號長\*,無符號長,size_t) \*|
|[__movsw](movsw.md)||intrin.h|無效__movsw(無符號短\*,無符號短,size_t) \*|
|_mulx_u32|BMI [2]|immintrin.h|無符號 int _mulx_u32(無符號 int,無符號\*int, 無符號 int)|
|[__nop](nop.md)||intrin.h|void __nop(void)|
|__nvreg_restore_fence||intrin.h|void __nvreg_restore_fence(void)|
|__nvreg_save_fence||intrin.h|void __nvreg_save_fence(void)|
|[__outbyte](outbyte.md)||intrin.h|不__outbyte合法(無符號短,無符號)|
|[__outbytestring](outbytestring.md)||intrin.h|空__outbytestring(無符號短,無符號字元\*,無符號長)|
|[__outdword](outdword.md)||intrin.h|空__outdword(無符號短,無符號長)|
|[__outdwordstring](outdwordstring.md)||intrin.h|無效__outdwordstring(無符號短,無符號長\*,無符號長)|
|[__outword](outword.md)||intrin.h|空__outword(無符號短,無符號短)|
|[__outwordstring](outwordstring.md)||intrin.h|空__outwordstring(無符號短,無符號短\*,無符號長)|
|[_pdep_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_pdep_u32)|BMI [2]|immintrin.h|無符號int_pdep_u32(無符號int,無符號int)|
|[_pext_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_pext_u32)|BMI [2]|immintrin.h|無符號 int _pext_u32(無符號 int,無符號 int)|
|[__popcnt](popcnt16-popcnt-popcnt64.md)|POPCNT|intrin.h|unsigned int __popcnt(unsigned int)|
|[__popcnt16](popcnt16-popcnt-popcnt64.md)|POPCNT|intrin.h|unsigned short __popcnt16(unsigned short)|
|[_rdrand16_step](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_rdrand16_step)|RDRAND [2]|immintrin.h|_rdrand16_step(無符號短\*)|
|[_rdrand32_step](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_rdrand32_step)|RDRAND [2]|immintrin.h|int _rdrand32_step(無符\*號 int)|
|[_rdseed16_step](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_rdseed16_step)|RDSEED [2]|immintrin.h|int _rdseed16_step(無符\*號短 )|
|[_rdseed32_step](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_rdseed32_step)|RDSEED [2]|immintrin.h|int _rdseed32_step(無符\*號 int)|
|[__rdtsc](rdtsc.md)||intrin.h|未簽署__int64_rdtsc(\_不合法 )|
|[__rdtscp](rdtscp.md)|RDTSCP|intrin.h|沒有符號__int64_rdtscp(\_無符號的int)\*|
|[_ReadBarrier](readbarrier.md)||intrin.h|void _ReadBarrier(void)|
|[__readcr0](readcr0.md)||intrin.h|unsigned long __readcr0(void)|
|[__readcr2](readcr2.md)||intrin.h|unsigned long __readcr2(void)|
|[__readcr3](readcr3.md)||intrin.h|unsigned long __readcr3(void)|
|[__readcr4](readcr4.md)||intrin.h|unsigned long __readcr4(void)|
|[__readcr8](readcr8.md)||intrin.h|unsigned long __readcr8(void)|
|[__readdr](readdr.md)||intrin.h|unsigned __readdr(unsigned)|
|[__readeflags](readeflags.md)||intrin.h|unsigned __readeflags(void)|
|[__readfsbyte](readfsbyte-readfsdword-readfsqword-readfsword.md)||intrin.h|無符號字元__readfsbyte(無符號長)|
|[__readfsdword](readfsbyte-readfsdword-readfsqword-readfsword.md)||intrin.h|無符號長__readfsdword(無符號長)|
|[__readfsword](readfsbyte-readfsdword-readfsqword-readfsword.md)||intrin.h|無符號短__readfsword(無符號長)|
|[__readmsr](readmsr.md)||intrin.h|沒有符號__int64_readmsr(\_無符號長 )|
|[__readpmc](readpmc.md)||intrin.h|未簽署__int64_readpmc(\_無符號長 )|
|[_ReadWriteBarrier](readwritebarrier.md)||intrin.h|void _ReadWriteBarrier(void)|
|[_ReturnAddress](returnaddress.md)||intrin.h|空\*_ReturnAddress(空)|
|_rorx_u32|BMI [2]|immintrin.h|無符號 int _rorx_u32(無符號 int,無符號 int)|
|[_rotl16](rotl8-rotl16.md)||intrin.h|無符號短_rotl16(無符號短字元,無符號字元)|
|[_rotl8](rotl8-rotl16.md)||intrin.h|無符號字元_rotl8(無符號字元,無符號字元)|
|[_rotr16](rotr8-rotr16.md)||intrin.h|無符號短_rotr16(無符號短字元,無符號字元)|
|[_rotr8](rotr8-rotr16.md)||intrin.h|無符號字元_rotr8(無符號字元,無符號字元)|
|_rsm||intrin.h|void _rsm(void)|
|_sarx_i32|BMI [2]|immintrin.h|int _sarx_i32(int,無符號 int)|
|[__segmentlimit](segmentlimit.md)||intrin.h|無符號長__segmentlimit(無符號長)|
|_sgdt||intrin.h|不合法_sgdt\*(不合法 )|
|_shlx_u32|BMI [2]|immintrin.h|無符號 int _shlx_u32(無符號 int,無符號 int)|
|_shrx_u32|BMI [2]|immintrin.h|無符號int_shrx_u32(無符號int,無符號int)|
|[__sidt](sidt.md)||intrin.h|不合法__sidt\*(不合法 )|
|__slwpcb|LWP [1]|ammintrin.h|空白\*__slwpcb(空)|
|_stac|SMAP|intrin.h|void _stac(void)|
|_store_be_u16<br /><br /> [_storebe_i16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_storebe_i16&expand=5141)|MOVBE|immintrin.h|無效_store_be_u16(無效\*,無符號短);<br /><br /> 空_storebe_i16(空\*,短);[3]|
|_store_be_u32<br /><br /> [_storebe_i32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_storebe_i32&expand=5142)|MOVBE|immintrin.h|無效_store_be_u32(無效\*,無符號int);<br /><br /> 空_storebe_i32(無效\*,int);[3]|
|_Store_HLERelease|HLE [2]|immintrin.h|空_Store_HLERelease(長時間揮\*發,長)|
|_StorePointer_HLERelease|HLE [2]|immintrin.h|空_StorePointer_HLERelease(空\*\*揮\*發, 空)|
|[__stosb](stosb.md)||intrin.h|無效__stosb(無符號字元\*,無符號字元,size_t)|
|[__stosd](stosd.md)||intrin.h|空__stosd(無符號長\*,無符號長,size_t)|
|[__stosw](stosw.md)||intrin.h|空__stosw(無符號短\*,無符號短,size_t)|
|_subborrow_u16||intrin.h|無符號字元_subborrow_u16(無符號字元、無符號短、無符號短、無符號短\*)|
|[_subborrow_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_subborrow_u32)||intrin.h|無符號字元_subborrow_u32(無符號字元、無符號 int、無符號 int、無\*符號 int)|
|_subborrow_u8||intrin.h|無符號字元_subborrow_u8(無符號字元,無符號字元,無符號字元,無符號字元\*)|
|[__svm_clgi](svm-clgi.md)||intrin.h|void __svm_clgi(void)|
|[__svm_invlpga](svm-invlpga.md)||intrin.h|空__svm_invlpga(不\*合法 ,int)|
|[__svm_skinit](svm-skinit.md)||intrin.h|void __svm_skinit(int)|
|[__svm_stgi](svm-stgi.md)||intrin.h|void __svm_stgi(void)|
|[__svm_vmload](svm-vmload.md)||intrin.h|void __svm_vmload(size_t)|
|[__svm_vmrun](svm-vmrun.md)||intrin.h|void __svm_vmrun(size_t)|
|[__svm_vmsave](svm-vmsave.md)||intrin.h|void __svm_vmsave(size_t)|
|_t1mskc_u32|ABM [1]|ammintrin.h|unsigned int _t1mskc_u32(unsigned int)|
|[_tzcnt_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_tzcnt_u32)|BMI|ammintrin.h, immintrin.h|unsigned int _tzcnt_u32(unsigned int)|
|_tzmsk_u32|ABM [1]|ammintrin.h|unsigned int _tzmsk_u32(unsigned int)|
|[__ud2](ud2.md)||intrin.h|void __ud2(void)|
|[_udiv64](udiv64.md)||intrin.h|無符號 int \_udiv64(\_無符號_int64,無符號\*int,無符號 int)|
|[__ull_rshift](ull-rshift.md)||intrin.h|未簽名__int64 [帕斯卡/cdecl] \__ull_rshift(無\_符號 _int64,int)|
|[__vmx_off](vmx-off.md)||intrin.h|void __vmx_off(void)|
|[__vmx_vmptrst](vmx-vmptrst.md)||intrin.h|不合法__vmx_vmptrst(未\_簽署\*_int64 )|
|[__wbinvd](wbinvd.md)||intrin.h|void __wbinvd(void)|
|[_WriteBarrier](writebarrier.md)||intrin.h|void _WriteBarrier(void)|
|[__writecr0](writecr0.md)||intrin.h|void __writecr0(unsigned long)|
|[__writecr3](writecr3.md)||intrin.h|void __writecr3(unsigned long)|
|[__writecr4](writecr4.md)||intrin.h|void __writecr4(unsigned long)|
|[__writecr8](writecr8.md)||intrin.h|void __writecr8(unsigned long)|
|[__writedr](writedr.md)||intrin.h|無效__writedr(無符號,無符號)|
|[__writeeflags](writeeflags.md)||intrin.h|void __writeeflags(unsigned)|
|[__writefsbyte](writefsbyte-writefsdword-writefsqword-writefsword.md)||intrin.h|不合法__writefsbyte(無符號長,無符號)|
|[__writefsdword](writefsbyte-writefsdword-writefsqword-writefsword.md)||intrin.h|無效__writefsdword(無符號長,無符號長)|
|[__writefsword](writefsbyte-writefsdword-writefsqword-writefsword.md)||intrin.h|空__writefsword(無符號長,無符號短)|
|[__writemsr](writemsr.md)||intrin.h|無效__writemsr(無符號長,無符號\__int64)|
|[_xabort](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_xabort)|RTM [2]|immintrin.h|void _xabort(unsigned int)|
|[_xbegin](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_xbegin)|RTM [2]|immintrin.h|unsigned _xbegin(void)|
|[_xend](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_xend)|RTM [2]|immintrin.h|void _xend(void)|
|[_xgetbv](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_xgetbv)|XSAVE [2]|immintrin.h|unsigned __int64 _xgetbv(unsigned int)|
|[_xrstor](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_xrstor)|XSAVE [2]|immintrin.h|不合法_xrstor(\*不合法的,無\_符號 _int64)|
|[_xsave](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_xsave)|XSAVE [2]|immintrin.h|無效_xsave(無效\*,無符\_號 _int64)|
|[_xsaveopt](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_xsaveopt)|XSAVEOPT [2]|immintrin.h|不合法_xsaveopt\*(不合法的\_不合法 _int64 )|
|[_xsetbv](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_xsetbv)|XSAVE [2]|immintrin.h|無效_xsetbv(無符號int,無符號\__int64)|
|[_xtest](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_xtest)|XTEST [2]|immintrin.h|unsigned char _xtest(void)|

## <a name="see-also"></a>另請參閱

[編譯器內部函數](compiler-intrinsics.md)\
[ARM 內部函數](arm-intrinsics.md)\
[ARM64 內部函數](arm64-intrinsics.md)\
[x64 (amd64) 內用品](x64-amd64-intrinsics-list.md)
