# MATERI_DOCKING
Pengenalan docking dan tutorial moleculer docking antara EGFR (3W2S) dengan doxorubicin
Repository ini berisi file-file pendukung tutorial praktis molecular docking protein-small molecule menggunakan AutoDock Vina. Materi ini dipersiapkan sebagai bahan pembelajaran bagi mahasiswa yang ingin memahami alur kerja (pipeline) molecular docking secara langsung.

🛠️ Software yang Dibutuhkan
Sebelum menggunakan file dalam repository ini, pastikan software berikut sudah terinstal:
Software Fungsi Link 
AutoDock Vina Engine docking utama https://vina.scripps.eduMGLTools/AutoDockTools 
Preparasi protein dan ligan https://ccsb.scripps.edu/mgltools
Discovery Studio VisualizerVisualisasi hasil docking https://discover.3ds.comPyMOL 
Visualisasi struktur 3D https://pymol.org

```
MATERI_DOCKING/
├── LIGAN_UJI.sdf          # Struktur ligan uji (format awal dari PubChem)
├── LIGAN_UJI.pdb          # Ligan uji setelah konversi ke format PDB
├── LIGAN_UJI.pdbqt        # Ligan uji siap docking (sudah preparasi MGLTools)
│
├── NATIVE_LIGAN.pdb       # Ligan native dari struktur kristal PDB
├── NATIVE_LIGAN.pdbqt     # Ligan native siap re-docking
│
├── PROTEIN.pdb            # Struktur protein original dari RCSB PDB
├── PROTEIN_CLEAN.pdb      # Protein setelah dibersihkan (hapus air, HETATM)
├── PROTEIN_CLEAN.pdbqt    # Protein siap docking
│
├── CONFIG.txt             # File konfigurasi AutoDock Vina
│
├── REdocking_output.pdbqt # Output hasil re-docking validasi
├── Docking_output.pdbqt   # Output hasil docking ligan uji
├── hasil_docking.pdb      # Kompleks protein-ligan hasil terbaik
│
├── hasil_2d.png           # Visualisasi interaksi 2D
├── hasil_3d.png           # Visualisasi interaksi 3D
├── Nilai RMSD Re docking.jpg  # Dokumentasi nilai RMSD validasi
│
├── autodock4.exe          # AutoDock engine
├── autogrid4.exe          # AutoGrid engine
└── PanduanMolDock_EGFR_Doxoru...  # Panduan tutorial
```

1. Download struktur protein dari RCSB PDB
           ↓
2. Preparasi protein (MGLTools)
   - Hapus molekul air
   - Tambah atom hidrogen
   - Tambah Kollman charge
   - Simpan sebagai .pdbqt
           ↓
3. Preparasi ligan (MGLTools)
   - Download dari PubChem (.sdf)
   - Konversi ke .pdb
   - Tentukan rotatable bonds
   - Tambah Gasteiger charge
   - Simpan sebagai .pdbqt
           ↓
4. Tentukan Grid Box (binding site)
   - Buat CONFIG.txt
           ↓
5. Jalankan AutoDock Vina
   vina --config CONFIG.txt --log log.txt
           ↓
6. Validasi Re-docking
   - Bandingkan pose hasil docking vs ligan native
   - RMSD < 2 Å = metode valid ✅
           ↓
7. Analisis dan Visualisasi
   - Visualisasi 3D: PyMOL
   - Analisis interaksi 2D: Discovery Studio Visualizer
  
File Config   
receptor = PROTEIN.pdbqt
ligand = LIGAN_UJI.pdbqt
center_x = [koordinat x binding site]
center_y = [koordinat y binding site]
center_z = [koordinat z binding site]
size_x = [ukuran grid x]
size_y = [ukuran grid y]
size_z = [ukuran grid z]
exhaustiveness = 8
num_modes = 9
energy_range = 4

Trott, O., Olson, A.J. (2010). AutoDock Vina: improving the speed and accuracy of docking. Journal of Computational Chemistry, 31, 455–461.
Morris, G.M., et al. (2009). AutoDock4 and AutoDockTools4. Journal of Computational Chemistry, 30(16), 2785–2791.

Created by : Aurelia Bunga Calista & Muthiah Atiqoh
