# Farol DS — Biblioteca de Ícones

Ícones Farol vivem em `@farol-ds/react` com sufixo `Icon` (ex: `AiIcon`, `SearchIcon`).
Nos protótipos HTML, mapeie para SVG inline ou Lucide React.

## Regras de Uso

- Sempre `aria-hidden="true"` em ícones decorativos
- Ícones sem label visível: `aria-label` no elemento pai ou `<VisuallyHidden>` dentro
- Tamanhos: `xs`=16px · `sm`=20px · `md`=24px (padrão) · `lg`=32px
- Nunca emojis como ícones de UI

## Catálogo Completo (source: farol-ds/react/src/lib/icon/icons/)

### IA e Assistentes
| Farol | Lucide | Descrição |
|-------|--------|-----------|
| `AiIcon` | `Sparkles` | IA genérica |
| `AiEditIcon` | `PenLine` | Edição com IA |
| `AiSubscribedIcon` | `Sparkles` + check | IA assinada |
| `AiSkillDocDraftingIcon` | `FileEdit` | Rascunho com IA |
| `AiSkillDocReviewIcon` | `FileSearch` | Revisão com IA |
| `AiSkillLegalResearchIcon` | `Scale` | Pesquisa jurídica IA |
| `JusIaIcon` | (SVG próprio) | Logo Jus IA |
| `JusbrasilIcon` | (SVG próprio) | Logo Jusbrasil |

### Navegação
| Farol | Lucide | Descrição |
|-------|--------|-----------|
| `HomeIcon` | `Home` | Início |
| `MenuIcon` | `Menu` | Hamburguer |
| `AppsIcon` | `LayoutGrid` | Apps/menu grid |
| `SearchIcon` | `Search` | Busca |
| `FilterIcon` | `SlidersHorizontal` | Filtros |
| `SortIcon` | `ArrowUpDown` | Ordenar |
| `SortAscIcon` | `ArrowUp` | Crescente |
| `SortDescIcon` | `ArrowDown` | Decrescente |
| `OpenSidebarIcon` | `PanelLeftOpen` | Abrir sidebar |
| `CloseSidebarIcon` | `PanelLeftClose` | Fechar sidebar |
| `FullscreenIcon` | `Maximize2` | Tela cheia |
| `FullscreenActiveIcon` | `Minimize2` | Sair tela cheia |
| `NewTabIcon` | `ExternalLink` | Nova aba |
| `LinkIcon` | `Link` | Link externo |

### Setas e Direções
| Farol | Lucide |
|-------|--------|
| `ChevronDownIcon` | `ChevronDown` |
| `ChevronUpIcon` | `ChevronUp` |
| `ChevronLeftIcon` | `ChevronLeft` |
| `ChevronRightIcon` | `ChevronRight` |
| `ArrowUpIcon` | `ArrowUp` |
| `ArrowDownIcon` | `ArrowDown` |
| `ArrowLeftIcon` | `ArrowLeft` |
| `ArrowRightIcon` | `ArrowRight` |
| `ArrowLeftUpIcon` | `ArrowUpLeft` |
| `ArrowLeftDownIcon` | `ArrowDownLeft` |
| `ArrowRightUpIcon` | `ArrowUpRight` |
| `ArrowRightDownIcon` | `ArrowDownRight` |
| `CornerDownLeftIcon` | `CornerDownLeft` |
| `CornerDownRightIcon` | `CornerDownRight` |
| `CornerUpLeftIcon` | `CornerUpLeft` |
| `CornerUpRightIcon` | `CornerUpRight` |

### Ações
| Farol | Lucide | Descrição |
|-------|--------|-----------|
| `AddIcon` | `Plus` | Adicionar |
| `AddRoundIcon` | `PlusCircle` | Adicionar circular |
| `SubtractIcon` | `Minus` | Remover |
| `SubtractRoundIcon` | `MinusCircle` | Remover circular |
| `EditIcon` | `Edit2` | Editar |
| `WriteIcon` | `PenLine` | Escrever |
| `DeleteIcon` | `Trash2` | Excluir |
| `ArchiveIcon` | `Archive` | Arquivar |
| `CopyIcon` | `Copy` | Copiar |
| `UploadIcon` | `Upload` | Enviar arquivo |
| `DownloadIcon` | `Download` | Baixar |
| `ShareIcon` | `Share2` | Compartilhar |
| `SendIcon` | `Send` | Enviar mensagem |
| `PrintIcon` | `Printer` | Imprimir |
| `RefreshIcon` | `RefreshCw` | Atualizar |
| `RedoIcon` | `Redo` | Refazer |
| `UndoIcon` | `Undo` | Desfazer |
| `RepeatIcon` | `Repeat` | Repetir |
| `DragIcon` | `GripVertical` | Arrastar |
| `CloseIcon` | `X` | Fechar |
| `XIcon` | `X` | X/fechar (redes) |
| `ReplyIcon` | `Reply` | Responder |
| `ReplyAllIcon` | `ReplyAll` | Responder todos |

### Conteúdo e Arquivos
| Farol | Lucide | Descrição |
|-------|--------|-----------|
| `DocumentIcon` | `FileText` | Documento |
| `NewDocumentIcon` | `FilePlus` | Novo documento |
| `NoteIcon` | `StickyNote` | Nota |
| `NoteMultipleIcon` | `Files` | Múltiplas notas |
| `FileSearchIcon` | `FileSearch` | Busca em arquivo |
| `FileZipIcon` | `FileArchive` | Arquivo ZIP |
| `PdfIcon` | `FileType` | PDF |
| `WordIcon` | `FileType2` | Word/DOCX |
| `ImageIcon` | `Image` | Imagem |
| `VideoIcon` | `Video` | Vídeo |
| `FolderIcon` | `Folder` | Pasta |
| `FolderAddIcon` | `FolderPlus` | Nova pasta |
| `FolderMoveIcon` | `FolderInput` | Mover pasta |
| `CollectionIcon` | `Library` | Coleção |
| `AttachmentIcon` | `Paperclip` | Anexo |
| `QuotesIcon` | `Quote` | Citação |
| `BookIcon` | `Book` | Livro |

### Comunicação
| Farol | Lucide | Descrição |
|-------|--------|-----------|
| `EmailIcon` | `Mail` | E-mail |
| `EmailOpenIcon` | `MailOpen` | E-mail aberto |
| `MessageIcon` | `MessageCircle` | Mensagem |
| `CommentIcon` | `MessageSquare` | Comentário |
| `QuestionAnswerIcon` | `MessagesSquare` | Perguntas e respostas |
| `NotificationIcon` | `Bell` | Notificação |
| `NotificationOnIcon` | `BellRing` | Notificação ativa |
| `NotificationOffIcon` | `BellOff` | Notificação desativada |
| `PhoneIcon` | `Phone` | Telefone |
| `WhatsappIcon` | `MessageCircle` | WhatsApp |
| `MicIcon` | `Mic` | Microfone |
| `MicOffIcon` | `MicOff` | Microfone mudo |
| `HeadphoneIcon` | `Headphones` | Fone de ouvido |
| `RssIcon` | `Rss` | RSS feed |
| `InboxIcon` | `Inbox` | Caixa de entrada |

### Usuário e Identidade
| Farol | Lucide | Descrição |
|-------|--------|-----------|
| `UserIcon` | `User` | Usuário |
| `UserAddIcon` | `UserPlus` | Adicionar usuário |
| `UserHistoryIcon` | `UserClock` | Histórico de usuário |
| `UserInstitutionalIcon` | `Building` | Usuário institucional |
| `UserMultiIcon` | `Users` | Múltiplos usuários |
| `UserVoiceIcon` | `UserCheck` | Usuário com voz |
| `ContactsIcon` | `Users` | Contatos |
| `LogoutIcon` | `LogOut` | Sair |
| `LockIcon` | `Lock` | Bloqueado |
| `UnlockIcon` | `Unlock` | Desbloqueado |
| `ShieldIcon` | `Shield` | Segurança |
| `VerifiedIcon` | `BadgeCheck` | Verificado |

### Status e Feedback
| Farol | Lucide | Descrição |
|-------|--------|-----------|
| `CheckIcon` | `Check` | Check simples |
| `CheckDoubleIcon` | `CheckCheck` | Check duplo (lido) |
| `CheckRoundIcon` | `CheckCircle2` | Check circular |
| `StatusCompleteIcon` | `CheckCircle2` | Concluído |
| `StatusIncompleteIcon` | `Circle` | Incompleto |
| `StatusPartiallyIcon` | `CircleDashed` | Parcial |
| `AlertIcon` | `AlertCircle` | Alerta |
| `WarningIcon` | `AlertTriangle` | Aviso |
| `InformationIcon` | `Info` | Informação |
| `QuestionIcon` | `HelpCircle` | Dúvida |
| `FlagIcon` | `Flag` | Marcar |
| `ReportIcon` | `ClipboardList` | Relatório |
| `ReportErrorIcon` | `ClipboardX` | Relatório de erro |
| `PlaceholderIcon` | `Square` | Placeholder |

### Interação e Reação
| Farol | Lucide | Descrição |
|-------|--------|-----------|
| `LikeIcon` | `ThumbsUp` | Curtir |
| `LikeActiveIcon` | `ThumbsUp` (filled) | Curtido |
| `DislikeIcon` | `ThumbsDown` | Não curtir |
| `DislikeActiveIcon` | `ThumbsDown` (filled) | Não curtido |
| `HeartIcon` | `Heart` | Favorito/amor |
| `HeartActiveIcon` | `Heart` (filled) | Favoritado |
| `StarIcon` | `Star` | Estrela |
| `StarActiveIcon` | `Star` (filled) | Estrela ativa |
| `StarHalfIcon` | `StarHalf` | Meia estrela |
| `BookmarkIcon` | `Bookmark` | Salvar |
| `BookmarkActiveIcon` | `Bookmark` (filled) | Salvo |
| `PushpinIcon` | `Pin` | Fixar |
| `FireIcon` | `Flame` | Popular/trending |

### Negócios e Finanças
| Farol | Lucide | Descrição |
|-------|--------|-----------|
| `MoneyIcon` | `DollarSign` | Dinheiro |
| `CardIcon` | `CreditCard` | Cartão |
| `CouponIcon` | `Ticket` | Cupom |
| `PixIcon` | `Zap` | Pix |
| `GiftIcon` | `Gift` | Presente |
| `BagIcon` | `ShoppingBag` | Sacola |
| `BasketIcon` | `ShoppingCart` | Carrinho |
| `TagIcon` | `Tag` | Etiqueta |
| `TagAddIcon` | `TagPlus` (custom) | Adicionar tag |
| `TagMultiIcon` | `Tags` | Múltiplas tags |
| `StatisticIcon` | `BarChart2` | Estatística |

### Jurídico (exclusivos Jusbrasil)
| Farol | Lucide | Descrição |
|-------|--------|-----------|
| `ScalesIcon` | `Scale` | Balança da Justiça |
| `CourtIcon` | `Building2` | Tribunal |
| `JudgeIcon` | `Gavel` | Juiz |
| `JudicialBranchIcon` | `Landmark` | Poder Judiciário |
| `CaseIcon` | `Briefcase` | Processo/caso |
| `HammerIcon` | `Gavel` | Martelo (decisão) |
| `LawyerDirectoryIcon` | `Users` | Diretório OAB |
| `SearchBookIcon` | `BookSearch` | Pesquisa jurídica |
| `FeedIcon` | `Newspaper` | Feed de notícias |
| `NewsIcon` | `Newspaper` | Notícia |
| `NewspaperIcon` | `Newspaper` | Jornal |
| `AcademyIcon` | `GraduationCap` | Academia/educação |

### Tempo e Dados
| Farol | Lucide | Descrição |
|-------|--------|-----------|
| `ClockIcon` | `Clock` | Hora |
| `TimerIcon` | `Timer` | Cronômetro |
| `CalendarIcon` | `Calendar` | Calendário |
| `CalendarEventIcon` | `CalendarDays` | Evento no calendário |
| `HistoryIcon` | `History` | Histórico |

### Tecnologia e Dispositivos
| Farol | Lucide | Descrição |
|-------|--------|-----------|
| `ComputerIcon` | `Monitor` | Desktop |
| `LaptopIcon` | `Laptop` | Notebook |
| `TabletIcon` | `Tablet` | Tablet |
| `SmartphoneIcon` | `Smartphone` | Celular |
| `CameraIcon` | `Camera` | Câmera |
| `QrCodeIcon` | `QrCode` | QR Code |
| `LightbulbIcon` | `Lightbulb` | Ideia |
| `PuzzleIcon` | `Puzzle` | Integração/plugin |
| `SettingsIcon` | `Settings` | Configurações |
| `DarkModeIcon` | `Moon` | Modo escuro |
| `LightModeIcon` | `Sun` | Modo claro |

### Tipografia e Editor
| Farol | Lucide | Descrição |
|-------|--------|-----------|
| `BoldIcon` | `Bold` | Negrito |
| `ItalicIcon` | `Italic` | Itálico |
| `ListOrderedIcon` | `ListOrdered` | Lista numerada |
| `ListUnorderedIcon` | `List` | Lista |
| `FontSizeIcon` | `Type` | Tamanho da fonte |

### Mídia e Áudio
| Farol | Lucide | Descrição |
|-------|--------|-----------|
| `PlayIcon` | `Play` | Reproduzir |
| `PauseIcon` | `Pause` | Pausar |
| `StopIcon` | `Square` | Parar |
| `VolumeUpIcon` | `Volume2` | Volume alto |
| `VolumeDownIcon` | `Volume1` | Volume baixo |
| `VolumeMuteIcon` | `VolumeX` | Mudo |

### Localização
| Farol | Lucide | Descrição |
|-------|--------|-----------|
| `LocationIcon` | `MapPin` | Local |
| `EarthIcon` | `Globe` | Mundo/global |

### Visibilidade
| Farol | Lucide | Descrição |
|-------|--------|-----------|
| `EyeIcon` | `Eye` | Ver |
| `EyeOffIcon` | `EyeOff` | Esconder |

### Redes Sociais
| Farol | Lucide | Descrição |
|-------|--------|-----------|
| `FacebookIcon` | `Facebook` | Facebook |
| `InstagramIcon` | `Instagram` | Instagram |
| `LinkedinIcon` | `Linkedin` | LinkedIn |
| `XIcon` | `Twitter` | X (Twitter) |
| `YoutubeIcon` | `Youtube` | YouTube |
| `WhatsappIcon` | `MessageCircle` | WhatsApp |

### Mais opções
| Farol | Lucide |
|-------|--------|
| `MoreHorizontalconIcon` | `MoreHorizontal` |
| `MoreVerticalIcon` | `MoreVertical` |

---

## Uso em HTML inline (protótipos)

Para protótipos HTML sem React, use SVG inline baseado nos tamanhos:

```html
<!-- 16px (xs) — dentro de badges/chips -->
<svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" aria-hidden="true">
  ...
</svg>

<!-- 20px (sm) — navegação, botões -->
<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" aria-hidden="true">
  ...
</svg>

<!-- 24px (md, padrão) — ícones de destaque -->
<svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" aria-hidden="true">
  ...
</svg>

<!-- 32px (lg) — ícones de feature/hero -->
<svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" aria-hidden="true">
  ...
</svg>
```

## Ícones mais usados nos protótipos

**Jurídico**: `ScalesIcon` → `Scale` · `CourtIcon` → `Building2` · `CaseIcon` → `Briefcase` · `HammerIcon` → `Gavel` · `JudicialBranchIcon` → `Landmark`

**Ações comuns**: `SearchIcon` → `Search` · `FilterIcon` → `SlidersHorizontal` · `DownloadIcon` → `Download` · `ShareIcon` → `Share2` · `BookmarkIcon` → `Bookmark`

**IA**: `AiIcon` → `Sparkles` · `AiEditIcon` → `PenLine` · `AiSkillLegalResearchIcon` → `Scale`

**Status**: `CheckRoundIcon` → `CheckCircle2` · `WarningIcon` → `AlertTriangle` · `InformationIcon` → `Info`

**Usuário**: `UserIcon` → `User` · `ContactsIcon` → `Users` · `LogoutIcon` → `LogOut`
