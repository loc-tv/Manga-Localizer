# Manga-Localizer
AI-assisted manga localization workstation focused on high-quality Vietnamese translation, context-aware dialogue adaptation, and professional manga typesetting.

Manga-Localizer/
│
├── app/                          # Application bootstrap & orchestration layer
│   ├── app.py                    # Main application entry controller
│   ├── startup.py                # Startup initialization sequence
│   ├── state_manager.py          # Global runtime state management
│   ├── task_queue.py             # Background OCR/translation task queue
│   ├── event_bus.py              # Inter-module event communication
│   └── dependency_container.py   # Service dependency injection
│
├── core/                         # Core business logic (UI-independent)
│   │
│   ├── database/                 # SQLite database layer
│   │   ├── db.py                 # Database connection manager
│   │   ├── schema.sql            # Database schema definitions
│   │   ├── migrations.py         # Database migration utilities
│   │   └── repositories/         # Repository pattern data access
│   │       ├── pages_repo.py
│   │       ├── ocr_repo.py
│   │       ├── translation_repo.py
│   │       └── character_repo.py
│   │
│   ├── models/                   # Internal data models
│   │   ├── page.py
│   │   ├── bubble.py
│   │   ├── character.py
│   │   ├── translation_chunk.py
│   │   └── typography_layout.py
│   │
│   ├── cache/                    # Runtime cache systems
│   │   ├── translation_cache.py
│   │   ├── image_cache.py
│   │   └── thumbnail_cache.py
│   │
│   ├── localization/             # Context-aware localization engine
│   │   ├── scene_builder.py          # Manga scene chunking
│   │   ├── character_memory.py       # Character personality inference
│   │   ├── relationship_tracker.py   # Relationship & hierarchy tracking
│   │   ├── pronoun_engine.py         # Dynamic Vietnamese pronoun switching
│   │   ├── emotion_detector.py       # Emotion inference from punctuation/dialogue
│   │   └── context_compressor.py     # Token-efficient context compression
│   │
│   ├── typography/               # Manga typography & layout engine
│   │   ├── phrase_chunker.py         # Semantic phrase segmentation
│   │   ├── line_breaker.py           # Candidate line break generation
│   │   ├── layout_solver.py          # Bubble layout optimization
│   │   ├── bubble_shape.py           # Bubble contour analysis
│   │   ├── font_manager.py           # Font loading & management
│   │   ├── emotion_typography.py     # Emotion-aware typography styling
│   │   ├── text_metrics.py           # Text measurement utilities
│   │   └── renderer.py               # Final text rendering engine
│   │
│   ├── bubble/                   # Speech bubble detection pipeline
│   │   ├── contour_detector.py       # Contour-based bubble detection
│   │   ├── mask_generator.py         # Bubble mask generation
│   │   ├── contour_refiner.py        # Contour cleanup/refinement
│   │   └── bubble_classifier.py      # Bubble type classification
│   │
│   ├── translation/              # LLM translation pipeline
│   │   ├── gemini_client.py          # Gemini API integration
│   │   ├── chunk_builder.py          # Translation chunk builder
│   │   ├── translation_pipeline.py   # Multi-pass translation workflow
│   │   ├── consistency_checker.py    # Translation consistency validation
│   │   └── prompt_builder.py         # Prompt construction system
│   │
│   ├── ocr/                      # OCR processing pipeline
│   │   ├── manga_ocr_engine.py       # MangaOCR integration
│   │   ├── image_preprocess.py       # OCR preprocessing filters
│   │   ├── bubble_cropper.py         # Bubble image cropping
│   │   └── reading_order.py          # Japanese manga reading order detection
│   │
│   ├── rendering/                # Final page rendering/export pipeline
│   │   ├── inpaint.py                # Bubble cleaning & text removal
│   │   ├── page_renderer.py          # Final page compositor
│   │   ├── export_png.py             # PNG export utilities
│   │   ├── export_pdf.py             # PDF export utilities
│   │   └── preview_renderer.py       # Real-time preview rendering
│   │
│   └── utils/                    # Shared utility helpers
│
├── engines/                      # External engine wrappers & adapters
│   ├── mangaocr/                 # MangaOCR wrapper layer
│   ├── gemini/                   # Gemini API wrapper layer
│   └── opencv/                   # OpenCV processing adapters
│
├── ui/                           # Desktop UI layer (PySide6)
│   │
│   ├── main_window.py            # Main application window
│   │
│   ├── pages/                    # Main workflow screens
│   │   ├── import_page.py            # Raw image import screen
│   │   ├── ocr_page.py               # OCR processing screen
│   │   ├── translation_page.py       # Translation monitoring screen
│   │   ├── editor_page.py            # Bubble editing workspace
│   │   └── export_page.py            # Export settings screen
│   │
│   ├── widgets/                  # Reusable UI widgets
│   │   ├── image_viewer.py           # Manga page image viewer
│   │   ├── bubble_overlay.py         # Bubble overlay renderer
│   │   ├── typography_preview.py     # Typography live preview
│   │   ├── translation_table.py      # Translation table/grid
│   │   └── progress_console.py       # Real-time processing logs
│   │
│   ├── dialogs/                  # Modal dialogs & popups
│   │
│   ├── panels/                   # Side panels & inspectors
│   │   ├── character_panel.py        # Character memory inspector
│   │   ├── font_panel.py             # Font & typography controls
│   │   ├── bubble_panel.py           # Bubble editing controls
│   │   └── project_panel.py          # Project metadata panel
│   │
│   ├── themes/                   # UI themes/stylesheets
│   └── resources/                # UI assets/resources
│
├── assets/                       # Static bundled assets
│   ├── fonts/                    # Vietnamese manga font packs
│   │   ├── dialogue/
│   │   ├── narration/
│   │   ├── emotion/
│   │   └── ui/
│   │
│   ├── icons/                    # Application icons
│   ├── themes/                   # Theme resources
│   └── templates/                # Export/layout templates
│
├── projects/                     # User localization projects
│   └── my_project/
│       ├── raw/                  # Original manga pages
│       ├── masks/                # Bubble masks
│       ├── cleaned/              # Cleaned pages after text removal
│       ├── rendered/             # Final rendered pages
│       ├── thumbnails/           # Cached thumbnails
│       ├── exports/              # Exported archives/output
│       └── project.db            # Project-local SQLite database
│
├── models/                       # AI model weights & checkpoints
│   ├── mangaocr/
│   └── detection/
│
├── tests/                        # Automated test suites
│   ├── typography/
│   ├── translation/
│   ├── ocr/
│   └── rendering/
│
├── scripts/                      # Development & utility scripts
│   ├── setup_env.py              # Development environment setup
│   ├── preload_models.py         # Model downloader/preloader
│   └── build_release.py          # Application packaging script
│
├── config/                       # Configuration files
│   ├── default.yaml              # Global application settings
│   ├── typography.yaml           # Typography/layout configuration
│   └── translation.yaml          # Translation/localization settings
│
├── temp/                         # Temporary runtime processing files
│
├── logs/                         # Application logs
│   ├── app.log
│   ├── ocr.log
│   └── translation.log
│
├── main.py                       # Main application entry point
├── requirements.txt              # Python dependencies
├── pyproject.toml                # Modern Python project configuration
├── README.md                     # Project documentation
├── .gitignore                    # Git ignore rules
└── .env                          # Environment variables & API keys


# Directory Overview
| Directory   | Purpose                                                   |
| ----------- | --------------------------------------------------------- |
| `app/`      | Application orchestration and runtime lifecycle           |
| `core/`     | Main localization, OCR, typography, and translation logic |
| `engines/`  | External AI/model wrappers                                |
| `ui/`       | PySide6 desktop interface                                 |
| `assets/`   | Fonts, icons, templates, themes                           |
| `projects/` | User manga localization projects                          |
| `models/`   | AI model weights                                          |
| `tests/`    | Automated testing                                         |
| `scripts/`  | Development and build scripts                             |
| `config/`   | YAML configuration system                                 |
| `temp/`     | Temporary runtime data                                    |
| `logs/`     | Application logging system                                |
