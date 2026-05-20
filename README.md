# Awesome-4D-Scene-Reconstruction

[![Awesome Logo](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)
<!--![Counter](https://api.infinitescript.com/badgen/count?name=hzxie/awesome/SceneGen) -->
<!--[![arXiv](https://img.shields.io/badge/arXiv-2505.05474-b31b1b.svg)](https://arxiv.org/abs/2505.05474)-->

# Overview

This repository collects summaries of over 100 recent studies on NeRF- or GS-based 4D scene reconstruction, along with the downstream applications, and will be continuously updated.

If you have suggestions for new resources, improvements to methodologies, or corrections for broken links, please don't hesitate to open an [issue]([https://github.com/ZiyangYan/Awesome-4D-Scene-Reconstruction/issues]) or submit a [pull request](https://github.com/hzxie/Awesome-4D-Scene-Reconstruction/pulls). Contributions of all kinds are welcome and greatly appreciated.

![4D-Scene-Reconstruction-Teaser](assets/4d_reconstruction_history.png)

### Table of Contents

- [Methods: A Hierarchical Taxonomy](#methods-a-hierarchical-taxonomy)
  - [Procedural Generation](#procedural-generation)
    - [Rule-based Generation](#rule-based-generation)
    - [Optimization-based Generation](#optimization-based-generation)
    - [LLM-based Generation](#llm-based-generation)
  - [Neural-3D Generation](#neural-3d-generation)
    - [Scene Parameters](#scene-parameters)
    - [Scene Graph](#scene-graph)
    - [Semantic Layout](#semantic-layout)
    - [Implicit Layout](#implicit-layout)
  - [Image-based Generation](#image-based-generation)
    - [Holistic Generation](#holistic-generation)
    - [Iterative Generation](#iterative-generation)
  - [Video-based Generation](#video-based-generation)
    - [Two-stage Generation](#two-stage-generation)
    - [One-stage Generation](#one-stage-generation)
- [Datasets](#datasets)
    - [Indoor Datasets](#indoor-datasets)
    - [Natural Datasets](#natural-datasets)
    - [Urban Datasets](#urban-datasets)

# Methods: A Hierarchical Taxonomy


# 4D Dynamic Scene Reconstruction System Overview

We categorize the different methods into **NeRF-style** and **GS-style** frameworks.

### NeRF-based Reconstruction

| Section | Method | Venue | Scenario | 4D-style | Scene Encoding | Geometry Representation | Text | Flow | Normal | Segment. | Uncer. | Extra Prior | Link |
|:---------:|:--------:|:-------:|:---------:|:----------:|:----------------:|:------------------------:|:------:|:------:|:--------:|:----------:|:--------:|:------------:|:------:|
|         | D-NeRF | CVPR2021 | indoor | Deformation fields | MLP | density |  |  |  |  |  |  | [D-NeRF: Neural Radiance Fields for Dynamic Scenes](https://openaccess.thecvf.com/content/CVPR2021/papers/Li_Neural_Scene_Flow_Fields_for_Space-Time_View_Synthesis_of_Dynamic_CVPR_2021_paper.pdf) |
|         | NSFF | CVPR2021 | outdoor | 4D NeRF | MLP | density |  | ✅ |  |  |  | RAFT | [NSFF Paper](https://openaccess.thecvf.com/content/CVPR2021/papers/Li_Neural_Scene_Flow_Fields_for_Space-Time_View_Synthesis_of_Dynamic_CVPR_2021_paper.pdf) |
|         | Video-NeRF | CVPR2021 | outdoor | 4D NeRF | MLP | density |  |  |  |  |  |  | [Video-NeRF Paper](https://openaccess.thecvf.com/content/CVPR2021/papers/Xian_Space-Time_Neural_Irradiance_Fields_for_Free-Viewpoint_Video_CVPR_2021_paper.pdf) |
|         | NR-NeRF | CVPR2021 | outdoor | Deformation fields | MLP | density |  |  |  |  |  |  | [NR-NeRF Paper](https://openaccess.thecvf.com/content/ICCV2021/papers/Tretschk_Non-Rigid_Neural_Radiance_Fields_Reconstruction_and_Novel_View_Synthesis_of_ICCV_2021_paper.pdf) |
|         | STaR | CVPR2021 | indoor | Deformation fields | MLP | density |  |  |  |  |  |  | [STaR Paper](https://openaccess.thecvf.com/content/CVPR2021/papers/Yuan_STaR_Self-Supervised_Tracking_and_Reconstruction_of_Rigid_Objects_in_Motion_CVPR_2021_paper.pdf) |
|         | DynNeRF | ICCV2021 | outdoor | 4D NeRF | MLP | density |  | ✅ |  |  |  | RAFT | [DynNeRF Paper](https://arxiv.org/abs/2012.09790) |
|         | NeRFlow | ICCV2021 | indoor | 4D NeRF | MLP | density |  | ✅ |  |  |  | Farneback G. | [NeRFlow Paper](https://arxiv.org/pdf/2012.09790) |
|         | StreamRF | NIPS2022 | indoor | 4D feature volumes | voxel grid + MLP | density |  |  |  |  |  |  | [StreamRF Paper](https://arxiv.org/pdf/2210.14831) |
|         | NDR | NIPS2022 | indoor | Deformation fields | MLP | density |  |  |  |  |  |  | [NDR Paper](https://proceedings.neurips.cc/paper_files/paper/2022/file/06a52a54c8ee03cd86771136bc91eb1f-Paper-Conference.pdf) |
|         | DeVRF | NIPS2022 | indoor | 4D feature volumes | voxel grid + MLP | density |  | ✅ |  |  |  | RAFT | [DeVRF Paper](https://proceedings.neurips.cc/paper_files/paper/2022/file/eeb57fdf745eb31a3c7ef22c59a4661d-Paper-Conference.pdf) |
|         | HexPlane | CVPR2023 | indoor | 4D feature volumes | feature plane+MLP | density |  |  |  |  |  |  | [HexPlane Paper](https://openaccess.thecvf.com/content/CVPR2023/papers/Cao_HexPlane_A_Fast_Representation_for_Dynamic_Scenes_CVPR_2023_paper.pdf) |
|         | K-Planes | CVPR2023 | indoor | 4D feature volumes | feature plane+MLP | density |  |  |  |  |  |  | [K-Planes Paper](https://openaccess.thecvf.com/content/CVPR2023/papers/Fridovich-Keil_K-Planes_Explicit_Radiance_Fields_in_Space_Time_and_Appearance_CVPR_2023_paper.pdf) |
|         | NeRF-DS | CVPR2023 | indoor | Deformation fields | MLP | density |  |  | ✅ |  |  |  | [NeRF-DS Paper](https://openaccess.thecvf.com/content/CVPR2023/papers/Yan_NeRF-DS_Neural_Radiance_Fields_for_Dynamic_Specular_Objects_CVPR_2023_paper.pdf) |
|         | SUDS | CVPR2023 | outdoor | 4D feature volumes | hash grid + MLP | density |  | ✅ |  |  |  | RAFT & DINO | [SUDS Paper](https://arxiv.org/pdf/2303.14536) |
|         | robust-denrf | CVPR2023 | outdoor | Deformation fields | MLP | density |  | ✅ |  |  |  | RAFT | [robust-denrf Paper](https://openaccess.thecvf.com/content/CVPR2023/papers/Liu_Robust_Dynamic_Radiance_Fields_CVPR_2023_paper.pdf) |
|         | TIDNeRF | CVPR2023 | indoor | 4D feature volumes | hash grid + MLP | density |  |  |  |  |  |  | [TIDNeRF Paper](https://openaccess.thecvf.com/content/CVPR2023/papers/Park_Temporal_Interpolation_Is_All_You_Need_for_Dynamic_Neural_Radiance_CVPR_2023_paper.pdf) |
|         | RoDynRF    | CVPR2023   | outdoor | 4D feature volumes | voxel grid + MLP    | density |    | ✔  |    |    |    | RAFT   | [link](https://robust-dynrf.github.io/) |
|         | HyperReel  | CVPR2023   | indoor  | 4D feature volumes | feature planes + MLP | density |    |    |    |    |    |        | [link](https://arxiv.org/pdf/2301.02238) |
|         | Total-Recon | ICCV2023  | indoor  | Deformation fields | MLP                 | SDF     |    | ✔  |    |    |    | VCN    | [link](https://openaccess.thecvf.com/content/ICCV2023/papers/Song_Total-Recon_Deformable_Scene_Reconstruction_for_Embodied_View_Synthesis_ICCV_2023_paper.pdf) |
|         | MixVoxels  | ICCV2023   | outdoor | 4D feature volumes | voxel grid + MLP    | density |    |    |    |    |    |        | [link](https://openaccess.thecvf.com/content/ICCV2023/papers/Wang_Mixed_Neural_Voxels_for_Fast_Multi-view_Video_Synthesis_ICCV_2023_paper.pdf) |
|         | MonoNeRF   | ICCV2023   | outdoor | 4D NeRF            | MLP                 | density |    | ✔  |    |    |    | RAFT   | [link](https://github.com/tianfr/MonoNeRF?tab=readme-ov-file) |
|         | MSTH       | NIPS2023   | indoor  | 4D feature volumes | Hash-grid+MLP       | density |    |    |    |    |    | ✔      | [link](https://proceedings.neurips.cc/paper_files/paper/2023/file/df31126302921ca9351fab73923a172f-Paper-Conference.pdf) |
|         | NVFi       | NIPS2023   | outdoor | 4D feature volumes | feature planes + MLP | density |    |    |    |    |    |        | [link](https://arxiv.org/pdf/2312.06398) |
|         | NeRFPlayer | TVCG2023   | indoor  | 4D feature volumes | Hash-grid+MLP       | density |    |    |    |    |    |        | [link](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=10049689) |
|         | Sync-NeRF  | AAAI2024   | indoor  | 4D NeRF            | MLP                 | density |    |    |    |    |    |        | [link](https://github.com/seoha-kim/Sync-NeRF?tab=readme-ov-file) |
|         | BLiRF      | AAAI2024   | indoor  | 4D feature volumes | MLP                 | density |    |    |    |    |    |        | [link](https://arxiv.org/pdf/2302.13543) |
|         | Ced-NeRF        | AAAI2024   | indoor  | 4D feature volumes | Hash-grid+MLP       | density |    |    |    |    |    |        | [link](https://github.com/Linyou/Ced-NeRF) |
|         | LiDAR4D         | CVPR2024   | outdoor | 4D feature volumes | hybrid + MLP        | density |    | ✔  |    |    |    | flow MLP | [link](https://openaccess.thecvf.com/content/CVPR2024/papers/Zheng_LiDAR4D_Dynamic_Neural_Fields_for_Novel_Space-time_View_LiDAR_Synthesis_CVPR_2024_paper.pdf) |
|         | DaReNeRF        | CVPR2024   | indoor  | 4D feature volumes | feature plane+MLP   | density |    |    |    |    |    | MaskDWT | [link](https://openaccess.thecvf.com/content/CVPR2024/papers/Lou_DaReNeRF_Direction-aware_Representation_for_Dynamic_Scenes_CVPR_2024_paper.pdf) |
|         | 4DNDF           | CVPR2024   | outdoor | 4D NeRF            | hash grid + MLP     | TSDF    |    |    |    | ✔  |    |        | [link](https://openaccess.thecvf.com/content/CVPR2024/papers/Zhong_3D_LiDAR_Mapping_in_Dynamic_Environments_using_a_4D_Implicit_CVPR_2024_paper.pdf) |
|         | Gear-NeRF       | CVPR2024   | indoor  | 4D feature volumes | feature plane+MLP   | density |    |    |    | ✔  |    | SAM    | [link](https://openaccess.thecvf.com/content/CVPR2024/papers/Liu_Gear-NeRF_Free-Viewpoint_Rendering_and_Tracking_with_Motion-aware_Spatio-Temporal_Sampling_CVPR_2024_paper.pdf) |
|         | NeuRAD          | CVPR2024   | outdoor | 4D feature volumes | hash grid + MLP     | SDF     |    |    |    |    |    |        | [link](https://openaccess.thecvf.com/content/CVPR2024/papers/Tonderski_NeuRAD_Neural_Rendering_for_Autonomous_Driving_CVPR_2024_paper.pdf) |
|         | ml-nsg          | CVPR2024   | outdoor | 4D NeRF            | hash grid + MLP     | density |    |    |    |    |    |        | [link](https://openaccess.thecvf.com/content/CVPR2024/papers/Fischer_Multi-Level_Neural_Scene_Graphs_for_Dynamic_Urban_Environments_CVPR_2024_paper.pdf) |
|         | S-DyRF          | CVPR2024   | indoor  | 4D feature volumes | feature plane + MLP | density |    |    |    |    |    |        | [link](https://openaccess.thecvf.com/content/CVPR2024/papers/Li_S-DyRF_Reference-Based_Stylized_Radiance_Fields_for_Dynamic_Scenes_CVPR_2024_paper.pdf) |
|         | DyBluRF         | CVPR2024   | outdoor | Deformation fields | MLP                 | density |    | ✔  |    |    |    | RAFT   | [link](http://arxiv.org/abs/2403.10103) |
|         | RoDUS           | ECCV2024   | outdoor | 4D feature volumes | hash grid + MLP     | density |    | ✔  |    | ✔  |    |        | [link](https://arxiv.org/pdf/2403.09419) |
|         | EmerNeRF        | ICLR2024   | outdoor | 4D feature volumes | Hash-grid+MLP       | density |    | ✔  |    |    |    | DINOv2 | [link](https://arxiv.org/pdf/2311.02077) |
|         | OTNeRF          | ICLR2024   | indoor  | Temporal prior     | MLP                 | density |    |    |    |    |    |        | [link](https://www.amazon.science/publications/improving-the-convergence-of-dynamic-nerfs-via-optimal-transport) |
|         | SLS4D           | TVCG2024   | indoor  | 4D feature volumes | hybrid + MLP        | density |    |    |    |    |    |        | [link](https://arxiv.org/pdf/2312.09743) |
|         | DecouplingNeRF  | TVCG2024   | indoor  | 4D NeRF            | MLP                 | density |    | ✔  |    |    |    | NSFF   | [link](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=10612248&casa_token=ydXuNDBnXkAAAAAA:1dW8yHbOb4a7p7uUZqv2W-_2vayrcDr3z_1LYQ28DkgSZAFvaJPRL5-rYZZZEjGzPaj-UVw) |
|         | STGC-NeRF       | AAAI2025   | outdoor | Temporal prior     | Hier. features+MLP  | density |    | ✔  | ✔  |    |    | GMSF   | [link](https://github.com/PSYZ1234/STGC-NeRF) |
|         | DetNeRF         | AAAI2025   | outdoor | 4D NeRF            | MLP                 | density |    | ✔  |    |    |    | RAFT   | [link](https://arxiv.org/abs/2301.00411) |






### GS-based Reconstruction

| Method | Venue | Scenario | 4D-style | Scene Encoding | Geometry Representation | Text | Flow | Normal | Segment. | Uncer. | Extra Prior | Link |
|:--------:|:-------:|:---------:|:----------:|:----------------:|:------------------------:|:------:|:------:|:--------:|:----------:|:--------:|:------------:|:------:|
| ST-4DGS         | ACM SIGGRAPH 2024 | in.&out. |                | Gaussian Splatting | Density |    |    |    |    |    |                     | [link](https://github.com/wanglids/ST-4DGS) |
| SaRO-GS         | ACM MM2024      | indoor |                | Gaussian Splatting | Density |    |    |    |    |    |                     | [link](https://dl.acm.org/doi/pdf/10.1145/3664647.3681463) |
| GaussianFlow     | CVPR2024       | indoor |                | Gaussian Splatting | Density |    | ✔  |    |    |    | Videoflow           | [link](https://zerg-overmind.github.io/GaussianFlow.github.io/) |
| 4D-GS           | CVPR2024       | indoor |                | Gaussian Splatting | Density |    |    |    |    |    |                     | 4D Gaussian Splatting for Real-Time Dynamic Scene Rendering |
| AYG             | CVPR2024       | indoor |                | Gaussian Splatting | Density | ✔  |    |    |    |    | Stable Diffusion & DM MVDream | [link](https://research.nvidia.com/labs/toronto-ai/AlignYourGaussians/) |
| DeformGS        | CVPR2024       | indoor |                | Gaussian Splatting | Density |    |    |    |    |    |                     | [link](https://openaccess.thecvf.com/content/CVPR2024/papers/Yang_Deformable_3D_Gaussians_for_High-Fidelity_Monocular_Dynamic_Scene_Reconstruction_CVPR_2024_paper.pdf) |
| SC-GS           | CVPR2024       | in.&out. |               | Gaussian Splatting | Density |    |    |    |    |    |                     | [link](https://yihua7.github.io/SC-GS-web/) |
| 3DGStream       | CVPR2024       | indoor |                | Gaussian Splatting | Density |    |    |    |    |    |                     | 3DGStream |
| Deformable-3DGS | CVPR2024       | indoor |                | Gaussian Splatting | Density |    |    |    |    |    |                     | [link](https://github.com/ingra14m/Deformable-3D-Gaussians) |
| GaGS            | CVPR2024       | in.&out. |               | Gaussian Splatting | Density |    |    |    |    |    |                     | [link](https://arxiv.org/pdf/2404.06270) |
| DrivingGaussian | CVPR2024       | outdoor |               | Gaussian Splatting | Density |    |    |    |    |    |                     | [link](http://arxiv.org/abs/2312.07920) |
| HUGS            | CVPR2024       | outdoor |               | Gaussian Splatting | Density |    | ✔  |    |    |    | Unimatch            | [link](https://openaccess.thecvf.com/content/CVPR2024/papers/Zhou_HUGS_Holistic_Urban_3D_Scene_Understanding_via_Gaussian_Splatting_CVPR_2024_paper.pdf) |
| StreetGaussian  | ECCV2024       | outdoor |               | Gaussian Splatting | Density |    |    |    | ✔  |    | Video k-net         | [link](https://link.springer.com/chapter/10.1007/978-3-031-73464-9_10) |
| DynMF           | ECCV2024       | indoor |                | Gaussian Splatting | Density |    |    |    |    |    |                     | [link](https://arxiv.org/pdf/2312.00112) |
| CD-3DGS         | ECCV2024       | indoor |                | Gaussian Splatting | Density |    | ✔  |    |    |    | RAFT                | [link](https://arxiv.org/pdf/2311.12897) |
| Casual-FVS      | ECCV2024       | outdoor |               | Gaussian Splatting | Density |    | ✔  |    |    |    | RAFT & SAM          | [link](https://arxiv.org/pdf/2312.02135) |
| ED-3DGS         | ECCV2024       | in.&out. |               | Gaussian Splatting | Density |    |    |    |    |    |                     | [link](https://jeongminb.github.io/e-d3dgs/) |
| SwinGS          | ECCV2024       | indoor |                | Gaussian Splatting | Density |    | ✔  |    |    |    | RAFT                | [link](https://arxiv.org/pdf/2312.13308) |
| GSPrediction     | SIGGRAPH2024   | indoor  |                | Gaussian Splatting | Density |    |    |    |    |    |                        | [link](https://dl.acm.org/doi/pdf/10.1145/3641519.3657417) |
| Marbles          | SIGGRAPH ASIA 2024 | indoor |               | Gaussian Splatting | Density |    |    |    | ✔  |    | Trackanything          | [link](https://dl.acm.org/doi/pdf/10.1145/3680528.3687681) |
| AmbientGaussian  | SIGGRAPH 2024  | outdoor |                | Gaussian Splatting | Density |    |    |    |    |    |                        | [link](https://dl.acm.org/doi/pdf/10.1145/3641519.3657488) |
| UA-4DGS          | NIPS2024       | indoor  |                | Gaussian Splatting | Density |    |    |    |    | ✔  | BLIP & Stable Diffusion | [link](https://arxiv.org/pdf/2411.08879) |
| Grid4D           | NIPS2024       | indoor  |                | Gaussian Splatting | Density |    |    |    | ✔  |    |                        | [link](https://arxiv.org/abs/2410.20815) |
| Vidu4D           | NIPS2024       | indoor  |                | Gaussian Splatting | Density | ✔  |    |    |    |    |                        | [link](https://arxiv.org/pdf/2405.16822) |
| DreamScene4D     | NIPS2024       | outdoor |                | Gaussian Splatting | Density |    | ✔  |    | ✔  |    | Gmflow & Grounded SAM   | [link](https://nips.cc/virtual/2024/poster/94673) |
| 4DGS             | NIPS2024       | in.&out.|                | Gaussian Splatting | Density | ✔  | ✔  |    |    | ✔  | BLIP & Stable Diffusion | [link](https://nips.cc/virtual/2024/poster/96899) |
| Ex4DGS           | NIPS2024       | indoor  |                | Gaussian Splatting | Density |    |    |    |    |    |                        | [link](https://github.com/juno181/Ex4DGS) |
| HiCoM            | NIPS2024       | indoor  |                | Gaussian Splatting | Density |    |    |    |    |    |                        | [link](https://arxiv.org/pdf/2411.07541) |
| MotionGS         | NIPS2024       | indoor  |                | Gaussian Splatting | Density |    | ✔  |    |    |    | Gaussianflow           | [link](https://proceedings.neurips.cc/paper_files/paper/2024/file/b88318174aad2cc174a4e05ab6bfad80-Paper-Conference.pdf) |
| DN-4DGS          | NIPS2024       | in.&out.|                | Gaussian Splatting | Density |    |    |    |    |    |                        | [link](https://arxiv.org/pdf/2410.13607) |
| SP-GS            | ICML2024       | indoor  |                | Gaussian Splatting | Density |    |    |    |    |    |                        | [link](https://dnvtmf.github.io/SP_GS.github.io/) |
| Gflow            | AAAI2025       | outdoor |                | Gaussian Splatting | Density |    | ✔  |    |    |    | DUSt3R & UniMatch      | [link](https://arxiv.org/pdf/2405.18426) |
| EfficientGS      | AAAI2025       | indoor  |                | Gaussian Splatting | Density |    | ✔  |    |    |    | COLMAP                  | [link](https://ojs.aaai.org/index.php/AAAI/article/view/32460) |
| 4D LangSpat      | CVPR2025       | indoor  |                | Gaussian Splatting | Density | ✔  |    |    | ✔  |    | SAM & CLIP             | [link](https://4d-langsplat.github.io/) |
| Instant GS       | CVPR2025       | indoor  |                | Gaussian Splatting | Density |    | ✔  |    |    |    | GM-Flow                | [link](https://github.com/yjb6/IGS) |
| VoxelSplat       | CVPR2025       | outdoor |                | Gaussian Splatting | Density |    |    |    | ✔  |    |                        | [link](https://github.com/ZZY816/VoxelSplat) |
| DeSiRe-GS        | CVPR2025       | outdoor |                | Gaussian Splatting | Density |    |    | ✔  |    |    |                        | [link](https://openaccess.thecvf.com/content/CVPR2025/papers/Peng_DeSiRe-GS_4D_Street_Gaussians_for_Static-Dynamic_Decomposition_and_Surface_Reconstruction_CVPR_2025_paper.pdf) |
| BARD-GS          | CVPR2025       | indoor  |                | Gaussian Splatting | Density |    |    |    |    |    |                        | [link](https://openaccess.thecvf.com/content/CVPR2025/papers/Lu_BARD-GS_Blur-Aware_Reconstruction_of_Dynamic_Scenes_via_Gaussian_Splatting_CVPR_2025_paper.pdf) |
| 4DGC             | CVPR2025       | indoor  |                | Gaussian Splatting | Density |    |    |    |    |    |                        | [link](http://arxiv.org/abs/2503.18421) |
| Feature4X        | CVPR2025   | in.&out.|                | Gaussian Splatting | Density | ✔  |    |    | ✔  |    | SAM2 & GPT-4o           | [link](https://feature4x.github.io/) |
| MoDec-GS         | CVPR2025   | in.&out.|                | Gaussian Splatting | Density |    |    |    |    |    |                        | [link](https://openaccess.thecvf.com/content/CVPR2025/papers/Kwak_MoDec-GS_Global-to-Local_Motion_Decomposition_and_Temporal_Interval_Adjustment_for_Compact_CVPR_2025_paper.pdf) |
| SplatAD          | CVPR2025   | outdoor |                | Gaussian Splatting | Density |    |    |    |    |    |                        | [link](https://openaccess.thecvf.com/content/CVPR2025/papers/Hess_SplatAD_Real-Time_Lidar_and_Camera_Rendering_with_3D_Gaussian_Splatting_CVPR_2025_paper.pdf) |
| SplineGS         | CVPR2025   | outdoor |                | Gaussian Splatting | Density |    |    |    |    |    |                        | [link](http://arxiv.org/abs/2412.09982) |
| FreeGave         | CVPR2025   | indoor  |                | Gaussian Splatting | Density |    |    |    | ✔  |    | SAM                    | [link](https://openaccess.thecvf.com/content/CVPR2025/papers/Li_FreeGave_3D_Physics_Learning_from_Dynamic_Videos_by_Gaussian_Velocity_CVPR_2025_paper.pdf) |
| GIFStream        | CVPR2025   | indoor  |                | Gaussian Splatting | Density |    |    |    |    |    |                        | [link](https://arxiv.org/abs/2505.07539) |
| SplatFlow        | CVPR2025   | outdoor |                | Gaussian Splatting | Density |    |    |    |    |    |                        | [link](http://arxiv.org/abs/2411.15482) |
| Instruct-4DGS    | CVPR2025   | indoor  |                | Gaussian Splatting | Density |    |    |    |    |    |                        | [link](https://openaccess.thecvf.com/content/CVPR2025/papers/Kwon_Efficient_Dynamic_Scene_Editing_via_4D_Gaussian-based_Static-Dynamic_Separation_CVPR_2025_paper.pdf) |
| MoSca            | CVPR2025   | outdoor |                | Gaussian Splatting | Density |    | ✔  |    |    |    | RAFT                   | [link](http://arxiv.org/abs/2405.17421) |
| taylor_gaussian  | CVPR2025   | indoor  |                | Gaussian Splatting | Density |    |    |    |    |    |                        | [link](http://arxiv.org/abs/2412.04282) |
| WildGS-SLAM      | CVPR2025   | indoor  |                | Gaussian Splatting | Density |    | ✔  |    |    | ✔  | DROID-SLAM & DINOV2     | [link](https://openaccess.thecvf.com/content/CVPR2025/papers/Zheng_WildGS-SLAM_Monocular_Gaussian_Splatting_SLAM_in_Dynamic_Environments_CVPR_2025_paper.pdf) |
| SpectroMotion    | CVPR2025   | indoor  |                | Gaussian Splatting | Density |    |    | ✔  |    |    |                        | [link](https://arxiv.org/abs/2410.17249) |
| DriveDreamer4D   | CVPR2025   | outdoor |                | Gaussian Splatting | Density |    |    |    |    |    |                        | [link](https://arxiv.org/abs/2410.13571) |
| 4D-Fly           | CVPR2025   | indoor  |                | Gaussian Splatting | Density |    |    |    |    |    |                        | [link](https://diankun-wu.github.io/4D-Fly/) |
| SpectroMotion    | CVPR2025   | indoor  |                | Gaussian Splatting | Density |    |    |    |    |    |                        | [link](https://openaccess.thecvf.com/content/CVPR2025/papers/Fan_SpectroMotion_Dynamic_3D_Reconstruction_of_Specular_Scenes_CVPR_2025_paper.pdf) |
| Omnire           | ICLR2025   | outdoor |                | Gaussian Splatting | Density |    |    |    |    |    |                        | [link](https://arxiv.org/pdf/2408.16760) |
| MoDGS            | ICLR2025   | indoor  |                | Gaussian Splatting | Density |    | ✔  |    |    |    | RAFT & SAM2             | [link](https://arxiv.org/abs/2406.00434) |
| EMD              | ICCV2025   | outdoor |                | Gaussian Splatting | Density |    |    |    |    |    |                        | [link](https://arxiv.org/pdf/2411.15582) |
| Shape of Motion  | ICCV2025   | outdoor |                | Gaussian Splatting | Density |    |    |    |    |    |                        | [link](https://arxiv.org/abs/2407.13764) |
| MonoFusion       | ICCV2025   | indoor  |                | Gaussian Splatting | Density |    |    |    |    |    |                        | [link](https://arxiv.org/pdf/2507.23782) |
| ADC-GS           | IJCAI2025   | in.&out.|                | Gaussian Splatting | Density |    |    |    |    |    |                        | [link](https://ijcai-preprints.s3.us-west-1.amazonaws.com/2025/1356.pdf) |
| MAGS             | TCSVT2025  | indoor  |                | Gaussian Splatting | Density |    | ✔  |    | 


# Datasets

## Synthetic Datasets (Ground Truth Geometry/Motion)

|  Name  | Scene Type | Sensor Setup | Resolution | Frame Rate | Scene/Seq | Temporal Scale |
|:------:|:-----------:|:-------------:|:----------:|:----------:|:---------:|:--------------:|
| D-NeRF | Indoor | 1 Cam | 800×800 | - | 8 | 50–200 frames |
| ParticleNeRF | Indoor | 40 Cam | - | - | 6 | - |
| SS3DM | Autonomous Driving | 6 Cams + 5 LiDAR | - | 10 FPS | 28 | 13K frames |


## Real-world: Monocular & Sparse View

| Name | Scene Type | Sensor Setup | Resolution | Frame Rate | Scene/Seq | Temporal Scale |
|:----:|:-----------:|:-------------:|:----------:|:----------:|:---------:|:--------------:|
| DAVIS | Outdoor | 1 Cam | - | - | 150 | 10k frames total |
| HyperNeRF | Indoor/Outdoor | 1–2 Cams | 540×960 | 15 FPS | 17 | 8–15s/seq |
| DyCheck | Indoor | 1 iPhone + 7 Static | - | - | 14 | 200–500 frames |
| Stereo4D | Indoor/Outdoor | 2 Cams | Diverse | - | 200K clips | - |
| NeRF-DS | Outdoor | 2 Cams | - | - | 8 | - |

---

## Real-world: Dense Multi-view & Human-Centric

| Name | Scene Type | Sensor Setup | Resolution | Frame Rate | Scene/Seq | Temporal Scale |
|:----:|:-----------:|:-------------:|:----------:|:----------:|:---------:|:--------------:|
| Panoptic Studio | Indoor | 480 Cams | - | - | 5 | - |
| ENeRF-Outdoor | Outdoor | 18 Cams | - | - | 3 | 1200 frames |
| Neu3DV | Indoor | 18–21 Cams | 2704×2028 | 30 FPS | 6 | 10s/seq |
| Technicolor | Indoor (RGB-only) | 16 Cams | 2048×1088 | 25 FPS | 12 | - |
| NVIDIA Dynamic | Outdoor | 12 Cams | - | - | 7 | 90–200 frames |
| Meeting Room | Indoor | 13 Cams | 1280×720 | 30 FPS | 3 | 300 frames |
| Google Immersive | Indoor/Outdoor | ≤46 Cams | - | - | 15 | - |

---

## Real-world: Long Horizon & Multimodal

| Name | Scene Type | Sensor Setup | Resolution | Frame Rate | Scene/Seq | Temporal Scale |
|:----:|:-----------:|:-------------:|:----------:|:----------:|:---------:|:--------------:|
| Waymo Open | Autonomous Driving | 5 Cams + 5 LiDAR | 1920×1280 | 10 FPS | 1150 | ∼12M frames |
| nuScenes | Autonomous Driving | 6 Cams + LiDAR | 1600×900 | 12 FPS | 1000 | ∼5.5h |
| Argoverse 2 | Autonomous Driving | 7 Cams + LiDAR | 1920×1200 | 30 FPS | 1000 | ∼1000h |
| PandaSet | Autonomous Driving | 6 Cams + LiDAR | 1920×1080 | 20 FPS | 103 | ∼1h |
| OmniHD-Scenes | Autonomous Driving | 6C + LiDAR + 6R | Diverse | 15 FPS | 1501 | ∼30s/seq |
| KITTI | Autonomous Driving | 2 Stereo + LiDAR | 1242×375 | 10 FPS | 22 | ∼6h |
| WayveScenes101 | Autonomous Driving (RGB-only) | 5 Cams | - | 10 FPS | 101 | 20s/seq |



