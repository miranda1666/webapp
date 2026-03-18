import React, { useEffect, useMemo, useRef, useState } from 'react';
import { motion, AnimatePresence } from 'framer-motion';
import {
  Plus,
  Search,
  Settings,
  Moon,
  Sun,
  LayoutDashboard,
  CheckSquare,
  CalendarDays,
  BookOpen,
  Target,
  Trash2,
  GripVertical,
  ChevronDown,
  ChevronRight,
  Sparkles,
  Quote,
  Minus,
  Type,
  Heading1,
  Heading2,
  ListChecks,
  PanelTop,
  Hash,
  Filter,
  Palette,
  Clock3,
  BarChart3,
  Star,
  Home,
  NotebookPen,
  Flag,
  CheckCircle2,
  Circle,
  X,
  ArrowUpRight,
} from 'lucide-react';
import { Card, CardContent, CardHeader, CardTitle, CardDescription } from '@/components/ui/card';
import { Button } from '@/components/ui/button';
import { Input } from '@/components/ui/input';
import { Textarea } from '@/components/ui/textarea';
import { Checkbox } from '@/components/ui/checkbox';
import { Badge } from '@/components/ui/badge';
import { ScrollArea } from '@/components/ui/scroll-area';
import {
  Dialog,
  DialogContent,
  DialogHeader,
  DialogTitle,
  DialogDescription,
  DialogFooter,
} from '@/components/ui/dialog';
import { Tabs, TabsContent, TabsList, TabsTrigger } from '@/components/ui/tabs';
import { Select, SelectContent, SelectItem, SelectTrigger, SelectValue } from '@/components/ui/select';
import { Progress } from '@/components/ui/progress';

// ------------------------------------------------------------
// Types
// ------------------------------------------------------------
type ThemeMode = 'light' | 'dark';
type PageIcon = 'dashboard' | 'doc' | 'tasks' | 'calendar' | 'journal' | 'goals';
type WidgetType = 'tasks' | 'habits' | 'agenda' | 'goals' | 'journal' | 'focus';
type BlockType = 'text' | 'h1' | 'h2' | 'todo' | 'quote' | 'toggle' | 'divider';

type Task = {
  id: string;
  title: string;
  completed: boolean;
  dueDate: string;
  priority: 'low' | 'medium' | 'high';
  area: string;
};

type Habit = {
  id: string;
  name: string;
  streak: number;
  completedToday: boolean;
  target: number;
};

type Goal = {
  id: string;
  title: string;
  progress: number;
  deadline: string;
  area: string;
};

type JournalEntry = {
  id: string;
  date: string;
  title: string;
  content: string;
  mood: 'Great' | 'Good' | 'Okay' | 'Low';
};

type EventItem = {
  id: string;
  title: string;
  time: string;
  date: string;
  location: string;
};

type Block = {
  id: string;
  type: BlockType;
  text: string;
  checked?: boolean;
  open?: boolean;
};

type Page = {
  id: string;
  title: string;
  icon: PageIcon;
  description: string;
  blocks: Block[];
};

type AppState = {
  theme: ThemeMode;
  accent: string;
  pages: Page[];
  activePageId: string;
  tasks: Task[];
  habits: Habit[];
  goals: Goal[];
  journal: JournalEntry[];
  events: EventItem[];
  dashboardWidgets: WidgetType[];
};

// ------------------------------------------------------------
// Helpers
// ------------------------------------------------------------
const uid = () => Math.random().toString(36).slice(2, 10);

const todayISO = () => {
  const d = new Date();
  return `${d.getFullYear()}-${String(d.getMonth() + 1).padStart(2, '0')}-${String(d.getDate()).padStart(2, '0')}`;
};

const prettyDate = (value: string) => {
  if (!value) return 'No date';
  const d = new Date(value + 'T00:00:00');
  return d.toLocaleDateString(undefined, { weekday: 'short', month: 'short', day: 'numeric' });
};

const pageIconMap: Record<PageIcon, React.ReactNode> = {
  dashboard: <LayoutDashboard className="h-4 w-4" />,
  doc: <BookOpen className="h-4 w-4" />,
  tasks: <CheckSquare className="h-4 w-4" />,
  calendar: <CalendarDays className="h-4 w-4" />,
  journal: <NotebookPen className="h-4 w-4" />,
  goals: <Target className="h-4 w-4" />,
};

const blockTypeMeta: { type: BlockType; label: string; icon: React.ReactNode }[] = [
  { type: 'text', label: 'Text', icon: <Type className="h-4 w-4" /> },
  { type: 'h1', label: 'Heading 1', icon: <Heading1 className="h-4 w-4" /> },
  { type: 'h2', label: 'Heading 2', icon: <Heading2 className="h-4 w-4" /> },
  { type: 'todo', label: 'To-do', icon: <ListChecks className="h-4 w-4" /> },
  { type: 'quote', label: 'Quote', icon: <Quote className="h-4 w-4" /> },
  { type: 'toggle', label: 'Toggle', icon: <PanelTop className="h-4 w-4" /> },
  { type: 'divider', label: 'Divider', icon: <Minus className="h-4 w-4" /> },
];

const defaultState = (): AppState => ({
  theme: 'dark',
  accent: 'from-fuchsia-500 via-violet-500 to-cyan-400',
  activePageId: 'page-dashboard',
  dashboardWidgets: ['focus', 'tasks', 'agenda', 'habits', 'goals', 'journal'],
  pages: [
    {
      id: 'page-dashboard',
      title: 'Life OS',
      icon: 'dashboard',
      description: 'A calm, beautiful control center for everything important.',
      blocks: [
        { id: uid(), type: 'h1', text: 'Welcome back ✨' },
        { id: uid(), type: 'text', text: 'Your dashboard keeps your goals, tasks, notes, routines, and plans in one intentional space.' },
        { id: uid(), type: 'quote', text: 'Build a life that feels good to live, not just good to organize.' },
      ],
    },
    {
      id: 'page-plans',
      title: 'Weekly Planning',
      icon: 'doc',
      description: 'Sketch priorities, reflect, and structure the week.',
      blocks: [
        { id: uid(), type: 'h1', text: 'Weekly Reset' },
        { id: uid(), type: 'todo', text: 'Review last week', checked: true },
        { id: uid(), type: 'todo', text: 'Choose top 3 priorities', checked: false },
        { id: uid(), type: 'todo', text: 'Block time for deep work', checked: false },
        { id: uid(), type: 'divider', text: '' },
        { id: uid(), type: 'toggle', text: 'Wins to remember', open: true },
      ],
    },
    {
      id: 'page-journal',
      title: 'Journal Notes',
      icon: 'journal',
      description: 'Capture ideas, emotions, and observations.',
      blocks: [
        { id: uid(), type: 'h1', text: 'Today’s reflection' },
        { id: uid(), type: 'text', text: 'What mattered most today?' },
      ],
    },
  ],
  tasks: [
    { id: uid(), title: 'Finalize quarterly budget', completed: false, dueDate: todayISO(), priority: 'high', area: 'Work' },
    { id: uid(), title: 'Book dentist appointment', completed: false, dueDate: todayISO(), priority: 'medium', area: 'Health' },
    { id: uid(), title: 'Plan weekend dinner with friends', completed: true, dueDate: todayISO(), priority: 'low', area: 'Life' },
  ],
  habits: [
    { id: uid(), name: 'Read 20 minutes', streak: 8, completedToday: true, target: 7 },
    { id: uid(), name: 'Morning walk', streak: 5, completedToday: false, target: 5 },
    { id: uid(), name: 'Inbox zero', streak: 3, completedToday: false, target: 5 },
  ],
  goals: [
    { id: uid(), title: 'Launch personal website', progress: 72, deadline: '2026-06-15', area: 'Career' },
    { id: uid(), title: 'Run a 10K comfortably', progress: 41, deadline: '2026-08-01', area: 'Fitness' },
    { id: uid(), title: 'Build emergency fund', progress: 58, deadline: '2026-12-31', area: 'Finance' },
  ],
  journal: [
    { id: uid(), date: todayISO(), title: 'Grounded energy', content: 'Felt focused after protecting the first two hours of the morning for thoughtful work.', mood: 'Good' },
  ],
  events: [
    { id: uid(), title: 'Team sync', time: '09:30', date: todayISO(), location: 'Studio A' },
    { id: uid(), title: 'Workout', time: '18:00', date: todayISO(), location: 'Local gym' },
    { id: uid(), title: 'Dinner reservation', time: '20:00', date: todayISO(), location: 'Juniper House' },
  ],
});

const usePersistentState = () => {
  const [state, setState] = useState<AppState>(() => {
    try {
      const raw = localStorage.getItem('life-os-state-v1');
      return raw ? JSON.parse(raw) : defaultState();
    } catch {
      return defaultState();
    }
  });

  useEffect(() => {
    localStorage.setItem('life-os-state-v1', JSON.stringify(state));
  }, [state]);

  return [state, setState] as const;
};

function cn(...classes: Array<string | false | null | undefined>) {
  return classes.filter(Boolean).join(' ');
}

// ------------------------------------------------------------
// Main App
// ------------------------------------------------------------
export default function NotionInspiredLifeOS() {
  const [state, setState] = usePersistentState();
  const [search, setSearch] = useState('');
  const [showCommand, setShowCommand] = useState(false);
  const [showWidgetEditor, setShowWidgetEditor] = useState(false);

  useEffect(() => {
    const root = document.documentElement;
    if (state.theme === 'dark') {
      root.classList.add('dark');
    } else {
      root.classList.remove('dark');
    }
  }, [state.theme]);

  useEffect(() => {
    const onKeyDown = (e: KeyboardEvent) => {
      if ((e.metaKey || e.ctrlKey) && e.key.toLowerCase() === 'k') {
        e.preventDefault();
        setShowCommand((v) => !v);
      }
    };
    window.addEventListener('keydown', onKeyDown);
    return () => window.removeEventListener('keydown', onKeyDown);
  }, []);

  const filteredPages = useMemo(() => {
    return state.pages.filter((p) => p.title.toLowerCase().includes(search.toLowerCase()));
  }, [search, state.pages]);

  const activePage = state.pages.find((p) => p.id === state.activePageId) ?? state.pages[0];

  const completedTasks = state.tasks.filter((t) => t.completed).length;
  const totalTasks = state.tasks.length || 1;
  const focusScore = Math.round(
    ((completedTasks / totalTasks) * 40) +
      ((state.habits.filter((h) => h.completedToday).length / (state.habits.length || 1)) * 30) +
      ((state.goals.reduce((a, g) => a + g.progress, 0) / (state.goals.length || 1)) * 0.3)
  );

  const setAccent = (accent: string) => setState((s) => ({ ...s, accent }));

  const updateActivePage = (updater: (page: Page) => Page) => {
    setState((s) => ({
      ...s,
      pages: s.pages.map((p) => (p.id === s.activePageId ? updater(p) : p)),
    }));
  };

  const createPage = (preset?: Partial<Page>) => {
    const page: Page = {
      id: uid(),
      title: preset?.title ?? 'Untitled',
      description: preset?.description ?? 'A fresh page for ideas, plans, or notes.',
      icon: preset?.icon ?? 'doc',
      blocks: preset?.blocks ?? [
        { id: uid(), type: 'h1', text: 'New page' },
        { id: uid(), type: 'text', text: 'Start writing here…' },
      ],
    };
    setState((s) => ({
      ...s,
      pages: [...s.pages, page],
      activePageId: page.id,
    }));
  };

  const deletePage = (id: string) => {
    setState((s) => {
      const remaining = s.pages.filter((p) => p.id !== id);
      const nextId = s.activePageId === id ? remaining[0]?.id ?? '' : s.activePageId;
      return { ...s, pages: remaining.length ? remaining : [defaultState().pages[0]], activePageId: nextId || defaultState().pages[0].id };
    });
  };

  return (
    <div className={cn('min-h-screen w-full transition-colors', state.theme === 'dark' ? 'bg-zinc-950 text-zinc-50' : 'bg-stone-50 text-zinc-900')}>
      <div className="relative min-h-screen overflow-hidden">
        <div className={cn('absolute inset-0 opacity-20 blur-3xl', `bg-gradient-to-br ${state.accent}`)} />
        <div className="absolute inset-0 bg-[radial-gradient(circle_at_top,rgba(255,255,255,0.12),transparent_35%)] dark:bg-[radial-gradient(circle_at_top,rgba(255,255,255,0.06),transparent_25%)]" />

        <div className="relative grid min-h-screen grid-cols-1 lg:grid-cols-[280px_1fr]">
          <aside className="border-r border-white/10 bg-white/50 backdrop-blur-2xl dark:bg-zinc-950/50">
            <div className="flex h-full flex-col">
              <div className="border-b border-black/5 p-4 dark:border-white/10">
                <div className="mb-4 flex items-center justify-between">
                  <div>
                    <div className="flex items-center gap-2 text-sm font-medium text-zinc-500 dark:text-zinc-400">
                      <Sparkles className="h-4 w-4" />
                      Personal workspace
                    </div>
                    <h1 className="mt-1 text-xl font-semibold tracking-tight">Astra Life OS</h1>
                  </div>
                  <Button variant="ghost" size="icon" onClick={() => setState((s) => ({ ...s, theme: s.theme === 'dark' ? 'light' : 'dark' }))}>
                    {state.theme === 'dark' ? <Sun className="h-4 w-4" /> : <Moon className="h-4 w-4" />}
                  </Button>
                </div>

                <button
                  onClick={() => setShowCommand(true)}
                  className="flex w-full items-center gap-2 rounded-2xl border border-black/5 bg-white/70 px-3 py-2 text-left text-sm text-zinc-500 shadow-sm transition hover:bg-white dark:border-white/10 dark:bg-white/5 dark:text-zinc-400 dark:hover:bg-white/10"
                >
                  <Search className="h-4 w-4" />
                  Search or jump to page
                  <span className="ml-auto rounded-md border border-black/5 px-1.5 py-0.5 text-xs dark:border-white/10">⌘K</span>
                </button>
              </div>

              <ScrollArea className="flex-1 px-3 py-4">
                <div className="mb-4 px-2 text-xs font-medium uppercase tracking-[0.2em] text-zinc-500 dark:text-zinc-500">Overview</div>
                <div className="space-y-1">
                  <SidebarQuickLink icon={<Home className="h-4 w-4" />} label="Home" active={activePage?.id === 'page-dashboard'} onClick={() => setState((s) => ({ ...s, activePageId: 'page-dashboard' }))} />
                  <SidebarQuickLink icon={<CheckSquare className="h-4 w-4" />} label="Tasks" active={false} onClick={() => createPage({ title: 'Tasks Overview', icon: 'tasks', description: 'A dedicated page for task planning.' })} />
                  <SidebarQuickLink icon={<CalendarDays className="h-4 w-4" />} label="Calendar" active={false} onClick={() => createPage({ title: 'Calendar Notes', icon: 'calendar', description: 'Meeting notes, plans, and scheduling thoughts.' })} />
                </div>

                <div className="mb-4 mt-6 flex items-center justify-between px-2 text-xs font-medium uppercase tracking-[0.2em] text-zinc-500 dark:text-zinc-500">
                  Pages
                  <button className="rounded-md p-1 hover:bg-black/5 dark:hover:bg-white/10" onClick={() => createPage()}>
                    <Plus className="h-4 w-4" />
                  </button>
                </div>

                <div className="space-y-1">
                  {filteredPages.map((page) => (
                    <button
                      key={page.id}
                      onClick={() => setState((s) => ({ ...s, activePageId: page.id }))}
                      className={cn(
                        'group flex w-full items-center gap-2 rounded-2xl px-3 py-2 text-left text-sm transition',
                        page.id === activePage?.id
                          ? 'bg-black text-white shadow-lg shadow-black/10 dark:bg-white dark:text-zinc-900'
                          : 'hover:bg-black/5 dark:hover:bg-white/10'
                      )}
                    >
                      <span>{pageIconMap[page.icon]}</span>
                      <span className="flex-1 truncate">{page.title}</span>
                      {state.pages.length > 1 && page.id !== 'page-dashboard' && (
                        <span
                          className="opacity-0 transition group-hover:opacity-100"
                          onClick={(e) => {
                            e.stopPropagation();
                            deletePage(page.id);
                          }}
                        >
                          <Trash2 className="h-4 w-4" />
                        </span>
                      )}
                    </button>
                  ))}
                </div>

                <Card className="mt-6 rounded-3xl border-black/5 bg-white/70 shadow-xl dark:border-white/10 dark:bg-white/5">
                  <CardContent className="p-4">
                    <div className="mb-2 flex items-center gap-2 text-sm font-medium">
                      <Palette className="h-4 w-4" /> Theme glow
                    </div>
                    <div className="grid grid-cols-3 gap-2">
                      {[
                        'from-fuchsia-500 via-violet-500 to-cyan-400',
                        'from-emerald-400 via-teal-500 to-sky-400',
                        'from-orange-400 via-rose-500 to-fuchsia-500',
                        'from-blue-500 via-indigo-500 to-purple-500',
                        'from-lime-400 via-emerald-500 to-teal-500',
                        'from-zinc-400 via-stone-500 to-neutral-700',
                      ].map((accent) => (
                        <button
                          key={accent}
                          onClick={() => setAccent(accent)}
                          className={cn(
                            'h-10 rounded-2xl border transition',
                            state.accent === accent ? 'border-zinc-900 dark:border-white scale-95' : 'border-black/5 dark:border-white/10'
                          )}
                        >
                          <div className={cn('h-full w-full rounded-[15px] bg-gradient-to-br', accent)} />
                        </button>
                      ))}
                    </div>
                  </CardContent>
                </Card>
              </ScrollArea>
            </div>
          </aside>

          <main className="flex min-h-screen flex-col">
            <header className="sticky top-0 z-20 border-b border-black/5 bg-white/60 px-4 py-3 backdrop-blur-2xl dark:border-white/10 dark:bg-zinc-950/50 lg:px-8">
              <div className="flex flex-wrap items-center gap-3">
                <div className="flex min-w-0 flex-1 items-center gap-3">
                  <div className="flex h-10 w-10 items-center justify-center rounded-2xl border border-black/5 bg-white shadow-sm dark:border-white/10 dark:bg-white/5">
                    {pageIconMap[activePage?.icon || 'doc']}
                  </div>
                  <div className="min-w-0">
                    <div className="truncate text-lg font-semibold tracking-tight">{activePage?.title}</div>
                    <div className="truncate text-sm text-zinc-500 dark:text-zinc-400">{activePage?.description}</div>
                  </div>
                </div>

                <div className="flex items-center gap-2">
                  <Button variant="outline" className="rounded-2xl" onClick={() => setShowWidgetEditor(true)}>
                    <LayoutDashboard className="mr-2 h-4 w-4" /> Edit widgets
                  </Button>
                  <Button variant="outline" className="rounded-2xl" onClick={() => updateActivePage((page) => ({ ...page, blocks: [...page.blocks, { id: uid(), type: 'text', text: 'New block…' }] }))}>
                    <Plus className="mr-2 h-4 w-4" /> Add block
                  </Button>
                  <Button variant="ghost" size="icon" className="rounded-2xl">
                    <Settings className="h-4 w-4" />
                  </Button>
                </div>
              </div>
            </header>

            <div className="mx-auto flex w-full max-w-7xl flex-1 flex-col gap-6 px-4 py-6 lg:px-8">
              {activePage?.id === 'page-dashboard' ? (
                <DashboardView state={state} setState={setState} focusScore={focusScore} onCreatePage={createPage} />
              ) : (
                <PageEditor page={activePage} updateActivePage={updateActivePage} />
              )}
            </div>
          </main>
        </div>
      </div>

      <CommandPalette
        open={showCommand}
        onOpenChange={setShowCommand}
        pages={state.pages}
        onSelectPage={(id) => setState((s) => ({ ...s, activePageId: id }))}
        onCreatePage={() => createPage()}
      />

      <WidgetEditorDialog
        open={showWidgetEditor}
        onOpenChange={setShowWidgetEditor}
        widgets={state.dashboardWidgets}
        setWidgets={(widgets) => setState((s) => ({ ...s, dashboardWidgets: widgets }))}
      />
    </div>
  );
}

// ------------------------------------------------------------
// Sidebar
// ------------------------------------------------------------
function SidebarQuickLink({
  icon,
  label,
  active,
  onClick,
}: {
  icon: React.ReactNode;
  label: string;
  active: boolean;
  onClick: () => void;
}) {
  return (
    <button
      onClick={onClick}
      className={cn(
        'flex w-full items-center gap-2 rounded-2xl px-3 py-2 text-left text-sm transition',
        active ? 'bg-black text-white dark:bg-white dark:text-zinc-900' : 'hover:bg-black/5 dark:hover:bg-white/10'
      )}
    >
      {icon}
      <span>{label}</span>
    </button>
  );
}

// ------------------------------------------------------------
// Dashboard
// ------------------------------------------------------------
function DashboardView({
  state,
  setState,
  focusScore,
  onCreatePage,
}: {
  state: AppState;
  setState: React.Dispatch<React.SetStateAction<AppState>>;
  focusScore: number;
  onCreatePage: (preset?: Partial<Page>) => void;
}) {
  const completedTasks = state.tasks.filter((t) => t.completed).length;
  const todaysEvents = state.events.filter((e) => e.date === todayISO());
  const widgets = state.dashboardWidgets;

  const widgetComponents: Record<WidgetType, React.ReactNode> = {
    focus: <FocusWidget focusScore={focusScore} tasks={state.tasks} habits={state.habits} goals={state.goals} />,
    tasks: <TaskWidget state={state} setState={setState} />,
    agenda: <AgendaWidget events={state.events} setState={setState} />,
    habits: <HabitsWidget habits={state.habits} setState={setState} />,
    goals: <GoalsWidget goals={state.goals} setState={setState} />,
    journal: <JournalWidget entries={state.journal} setState={setState} />,
  };

  return (
    <div className="space-y-6">
      <section className="grid gap-4 xl:grid-cols-[1.3fr_0.7fr]">
        <Card className="overflow-hidden rounded-[28px] border-black/5 bg-white/70 shadow-2xl dark:border-white/10 dark:bg-white/5">
          <CardContent className="p-0">
            <div className={cn('relative overflow-hidden rounded-[28px] p-6 md:p-8', `bg-gradient-to-br ${state.accent}`)}>
              <div className="absolute inset-0 bg-black/10" />
              <div className="relative z-10 max-w-2xl text-white">
                <Badge className="mb-4 rounded-full border-white/20 bg-white/15 text-white backdrop-blur">Beautifully organized</Badge>
                <h2 className="text-3xl font-semibold tracking-tight md:text-4xl">A calmer, more aesthetic way to run your whole life.</h2>
                <p className="mt-3 max-w-xl text-sm text-white/90 md:text-base">
                  Plan work, track habits, manage responsibilities, and capture thoughts in one elegant workspace.
                </p>
                <div className="mt-6 flex flex-wrap gap-3">
                  <Button className="rounded-2xl bg-white text-zinc-900 hover:bg-white/90" onClick={() => onCreatePage({ title: 'New Strategy Page', icon: 'doc' })}>
                    <Plus className="mr-2 h-4 w-4" /> New page
                  </Button>
                  <Button variant="secondary" className="rounded-2xl border border-white/20 bg-white/10 text-white hover:bg-white/20" onClick={() => onCreatePage({ title: 'Meeting Notes', icon: 'calendar' })}>
                    <ArrowUpRight className="mr-2 h-4 w-4" /> Capture something
                  </Button>
                </div>
              </div>
            </div>
          </CardContent>
        </Card>

        <div className="grid gap-4 sm:grid-cols-3 xl:grid-cols-1">
          <MetricCard label="Tasks done" value={`${completedTasks}/${state.tasks.length}`} icon={<CheckCircle2 className="h-4 w-4" />} />
          <MetricCard label="Habits today" value={`${state.habits.filter((h) => h.completedToday).length}/${state.habits.length}`} icon={<Star className="h-4 w-4" />} />
          <MetricCard label="Events today" value={`${todaysEvents.length}`} icon={<Clock3 className="h-4 w-4" />} />
        </div>
      </section>

      <section className="grid gap-4 lg:grid-cols-2 2xl:grid-cols-3">
        {widgets.map((widget) => (
          <React.Fragment key={widget}>{widgetComponents[widget]}</React.Fragment>
        ))}
      </section>
    </div>
  );
}

function MetricCard({ label, value, icon }: { label: string; value: string; icon: React.ReactNode }) {
  return (
    <Card className="rounded-[26px] border-black/5 bg-white/70 shadow-xl dark:border-white/10 dark:bg-white/5">
      <CardContent className="flex items-center justify-between p-5">
        <div>
          <div className="text-sm text-zinc-500 dark:text-zinc-400">{label}</div>
          <div className="mt-1 text-2xl font-semibold tracking-tight">{value}</div>
        </div>
        <div className="flex h-11 w-11 items-center justify-center rounded-2xl border border-black/5 bg-white dark:border-white/10 dark:bg-white/10">
          {icon}
        </div>
      </CardContent>
    </Card>
  );
}

function FocusWidget({
  focusScore,
  tasks,
  habits,
  goals,
}: {
  focusScore: number;
  tasks: Task[];
  habits: Habit[];
  goals: Goal[];
}) {
  const completedTasks = tasks.filter((t) => t.completed).length;
  const completedHabits = habits.filter((h) => h.completedToday).length;
  const avgGoal = goals.length ? Math.round(goals.reduce((a, g) => a + g.progress, 0) / goals.length) : 0;

  return (
    <Card className="rounded-[28px] border-black/5 bg-white/70 shadow-xl dark:border-white/10 dark:bg-white/5">
      <CardHeader>
        <CardTitle className="flex items-center gap-2 text-lg"><BarChart3 className="h-5 w-5" /> Focus score</CardTitle>
        <CardDescription>Your daily momentum across priorities, habits, and outcomes.</CardDescription>
      </CardHeader>
      <CardContent className="space-y-4">
        <div className="flex items-end justify-between">
          <div>
            <div className="text-5xl font-semibold tracking-tight">{focusScore}</div>
            <div className="text-sm text-zinc-500 dark:text-zinc-400">out of 100</div>
          </div>
          <Badge className="rounded-full">Steady progress</Badge>
        </div>
        <Progress value={focusScore} className="h-2" />
        <div className="grid gap-3 sm:grid-cols-3">
          <MiniStat label="Tasks" value={`${completedTasks}/${tasks.length}`} />
          <MiniStat label="Habits" value={`${completedHabits}/${habits.length}`} />
          <MiniStat label="Goals" value={`${avgGoal}%`} />
        </div>
      </CardContent>
    </Card>
  );
}

function MiniStat({ label, value }: { label: string; value: string }) {
  return (
    <div className="rounded-2xl border border-black/5 bg-black/[0.03] p-3 dark:border-white/10 dark:bg-white/[0.03]">
      <div className="text-xs uppercase tracking-[0.16em] text-zinc-500">{label}</div>
      <div className="mt-1 text-lg font-semibold">{value}</div>
    </div>
  );
}

function TaskWidget({ state, setState }: { state: AppState; setState: React.Dispatch<React.SetStateAction<AppState>> }) {
  const [draft, setDraft] = useState('');
  const [priority, setPriority] = useState<'low' | 'medium' | 'high'>('medium');
  const [area, setArea] = useState('Life');

  const orderedTasks = [...state.tasks].sort((a, b) => Number(a.completed) - Number(b.completed));

  return (
    <Card className="rounded-[28px] border-black/5 bg-white/70 shadow-xl dark:border-white/10 dark:bg-white/5">
      <CardHeader>
        <CardTitle className="flex items-center gap-2 text-lg"><CheckSquare className="h-5 w-5" /> Tasks</CardTitle>
        <CardDescription>Fast capture with due dates, areas, and priorities.</CardDescription>
      </CardHeader>
      <CardContent className="space-y-4">
        <div className="flex flex-col gap-2 sm:flex-row">
          <Input value={draft} onChange={(e) => setDraft(e.target.value)} placeholder="Add a task…" className="rounded-2xl" />
          <Select value={priority} onValueChange={(v: 'low' | 'medium' | 'high') => setPriority(v)}>
            <SelectTrigger className="w-full rounded-2xl sm:w-[130px]"><SelectValue placeholder="Priority" /></SelectTrigger>
            <SelectContent>
              <SelectItem value="low">Low</SelectItem>
              <SelectItem value="medium">Medium</SelectItem>
              <SelectItem value="high">High</SelectItem>
            </SelectContent>
          </Select>
          <Button
            className="rounded-2xl"
            onClick={() => {
              if (!draft.trim()) return;
              setState((s) => ({
                ...s,
                tasks: [{ id: uid(), title: draft.trim(), completed: false, dueDate: todayISO(), priority, area }, ...s.tasks],
              }));
              setDraft('');
            }}
          >
            Add
          </Button>
        </div>

        <div className="space-y-2">
          {orderedTasks.map((task) => (
            <div key={task.id} className="flex items-start gap-3 rounded-2xl border border-black/5 bg-white/60 p-3 dark:border-white/10 dark:bg-white/[0.03]">
              <Checkbox
                checked={task.completed}
                onCheckedChange={(checked) =>
                  setState((s) => ({
                    ...s,
                    tasks: s.tasks.map((t) => (t.id === task.id ? { ...t, completed: Boolean(checked) } : t)),
                  }))
                }
              />
              <div className="min-w-0 flex-1">
                <div className={cn('font-medium', task.completed && 'text-zinc-400 line-through')}>{task.title}</div>
                <div className="mt-1 flex flex-wrap gap-2 text-xs text-zinc-500">
                  <Badge variant="secondary" className="rounded-full">{task.area}</Badge>
                  <Badge variant="outline" className="rounded-full">{task.priority}</Badge>
                  <span>{prettyDate(task.dueDate)}</span>
                </div>
              </div>
              <button
                onClick={() => setState((s) => ({ ...s, tasks: s.tasks.filter((t) => t.id !== task.id) }))}
                className="rounded-xl p-2 transition hover:bg-black/5 dark:hover:bg-white/10"
              >
                <Trash2 className="h-4 w-4" />
              </button>
            </div>
          ))}
        </div>
      </CardContent>
    </Card>
  );
}

function HabitsWidget({ habits, setState }: { habits: Habit[]; setState: React.Dispatch<React.SetStateAction<AppState>> }) {
  const [draft, setDraft] = useState('');

  return (
    <Card className="rounded-[28px] border-black/5 bg-white/70 shadow-xl dark:border-white/10 dark:bg-white/5">
      <CardHeader>
        <CardTitle className="flex items-center gap-2 text-lg"><Star className="h-5 w-5" /> Habits</CardTitle>
        <CardDescription>Track daily consistency and protect your momentum.</CardDescription>
      </CardHeader>
      <CardContent className="space-y-4">
        <div className="flex gap-2">
          <Input value={draft} onChange={(e) => setDraft(e.target.value)} placeholder="Add a habit…" className="rounded-2xl" />
          <Button
            className="rounded-2xl"
            onClick={() => {
              if (!draft.trim()) return;
              setState((s) => ({
                ...s,
                habits: [...s.habits, { id: uid(), name: draft.trim(), streak: 0, completedToday: false, target: 7 }],
              }));
              setDraft('');
            }}
          >
            Add
          </Button>
        </div>

        <div className="space-y-2">
          {habits.map((habit) => (
            <div key={habit.id} className="rounded-2xl border border-black/5 bg-white/60 p-4 dark:border-white/10 dark:bg-white/[0.03]">
              <div className="flex items-center justify-between gap-3">
                <div>
                  <div className="font-medium">{habit.name}</div>
                  <div className="mt-1 text-sm text-zinc-500">{habit.streak} day streak</div>
                </div>
                <Button
                  variant={habit.completedToday ? 'secondary' : 'outline'}
                  className="rounded-2xl"
                  onClick={() =>
                    setState((s) => ({
                      ...s,
                      habits: s.habits.map((h) =>
                        h.id === habit.id
                          ? {
                              ...h,
                              completedToday: !h.completedToday,
                              streak: h.completedToday ? Math.max(0, h.streak - 1) : h.streak + 1,
                            }
                          : h
                      ),
                    }))
                  }
                >
                  {habit.completedToday ? 'Done today' : 'Mark done'}
                </Button>
              </div>
              <div className="mt-3">
                <Progress value={(habit.streak / habit.target) * 100} className="h-2" />
              </div>
            </div>
          ))}
        </div>
      </CardContent>
    </Card>
  );
}

function AgendaWidget({
  events,
  setState,
}: {
  events: EventItem[];
  setState: React.Dispatch<React.SetStateAction<AppState>>;
}) {
  const [title, setTitle] = useState('');
  const [time, setTime] = useState('12:00');
  const [location, setLocation] = useState('');

  const todaysEvents = events
    .filter((e) => e.date === todayISO())
    .sort((a, b) => a.time.localeCompare(b.time));

  return (
    <Card className="rounded-[28px] border-black/5 bg-white/70 shadow-xl dark:border-white/10 dark:bg-white/5">
      <CardHeader>
        <CardTitle className="flex items-center gap-2 text-lg"><CalendarDays className="h-5 w-5" /> Agenda</CardTitle>
        <CardDescription>A light, integrated day view for commitments and plans.</CardDescription>
      </CardHeader>
      <CardContent className="space-y-4">
        <div className="grid gap-2 sm:grid-cols-[1fr_120px_1fr_auto]">
          <Input value={title} onChange={(e) => setTitle(e.target.value)} placeholder="Add event…" className="rounded-2xl" />
          <Input value={time} onChange={(e) => setTime(e.target.value)} type="time" className="rounded-2xl" />
          <Input value={location} onChange={(e) => setLocation(e.target.value)} placeholder="Location" className="rounded-2xl" />
          <Button
            className="rounded-2xl"
            onClick={() => {
              if (!title.trim()) return;
              setState((s) => ({
                ...s,
                events: [...s.events, { id: uid(), title: title.trim(), time, date: todayISO(), location }],
              }));
              setTitle('');
              setLocation('');
            }}
          >
            Add
          </Button>
        </div>

        <div className="space-y-2">
          {todaysEvents.length === 0 ? (
            <div className="rounded-2xl border border-dashed border-black/10 p-6 text-sm text-zinc-500 dark:border-white/10">
              Nothing scheduled for today.
            </div>
          ) : (
            todaysEvents.map((event) => (
              <div key={event.id} className="flex items-center gap-3 rounded-2xl border border-black/5 bg-white/60 p-3 dark:border-white/10 dark:bg-white/[0.03]">
                <div className="w-16 rounded-xl border border-black/5 bg-black/[0.03] px-2 py-2 text-center text-sm font-medium dark:border-white/10 dark:bg-white/[0.03]">
                  {event.time}
                </div>
                <div className="min-w-0 flex-1">
                  <div className="font-medium">{event.title}</div>
                  <div className="text-sm text-zinc-500">{event.location || 'No location'}</div>
                </div>
                <button
                  onClick={() => setState((s) => ({ ...s, events: s.events.filter((e) => e.id !== event.id) }))}
                  className="rounded-xl p-2 transition hover:bg-black/5 dark:hover:bg-white/10"
                >
                  <X className="h-4 w-4" />
                </button>
              </div>
            ))
          )}
        </div>
      </CardContent>
    </Card>
  );
}

function GoalsWidget({ goals, setState }: { goals: Goal[]; setState: React.Dispatch<React.SetStateAction<AppState>> }) {
  const [draft, setDraft] = useState('');

  return (
    <Card className="rounded-[28px] border-black/5 bg-white/70 shadow-xl dark:border-white/10 dark:bg-white/5">
      <CardHeader>
        <CardTitle className="flex items-center gap-2 text-lg"><Target className="h-5 w-5" /> Goals</CardTitle>
        <CardDescription>See progress clearly and move long-term projects forward.</CardDescription>
      </CardHeader>
      <CardContent className="space-y-4">
        <div className="flex gap-2">
          <Input value={draft} onChange={(e) => setDraft(e.target.value)} placeholder="New goal…" className="rounded-2xl" />
          <Button
            className="rounded-2xl"
            onClick={() => {
              if (!draft.trim()) return;
              setState((s) => ({
                ...s,
                goals: [...s.goals, { id: uid(), title: draft.trim(), progress: 0, deadline: todayISO(), area: 'Personal' }],
              }));
              setDraft('');
            }}
          >
            Add
          </Button>
        </div>

        <div className="space-y-3">
          {goals.map((goal) => (
            <div key={goal.id} className="rounded-2xl border border-black/5 bg-white/60 p-4 dark:border-white/10 dark:bg-white/[0.03]">
              <div className="flex items-start justify-between gap-4">
                <div className="min-w-0">
                  <div className="font-medium">{goal.title}</div>
                  <div className="mt-1 text-sm text-zinc-500">
                    {goal.area} · due {prettyDate(goal.deadline)}
                  </div>
                </div>
                <Badge className="rounded-full">{goal.progress}%</Badge>
              </div>
              <Progress value={goal.progress} className="mt-3 h-2" />
              <div className="mt-3 flex gap-2">
                <Button
                  variant="outline"
                  size="sm"
                  className="rounded-xl"
                  onClick={() =>
                    setState((s) => ({
                      ...s,
                      goals: s.goals.map((g) => (g.id === goal.id ? { ...g, progress: Math.max(0, g.progress - 10) } : g)),
                    }))
                  }
                >
                  -10
                </Button>
                <Button
                  size="sm"
                  className="rounded-xl"
                  onClick={() =>
                    setState((s) => ({
                      ...s,
                      goals: s.goals.map((g) => (g.id === goal.id ? { ...g, progress: Math.min(100, g.progress + 10) } : g)),
                    }))
                  }
                >
                  +10
                </Button>
              </div>
            </div>
          ))}
        </div>
      </CardContent>
    </Card>
  );
}

function JournalWidget({
  entries,
  setState,
}: {
  entries: JournalEntry[];
  setState: React.Dispatch<React.SetStateAction<AppState>>;
}) {
  const [title, setTitle] = useState('');
  const [content, setContent] = useState('');
  const [mood, setMood] = useState<JournalEntry['mood']>('Good');

  return (
    <Card className="rounded-[28px] border-black/5 bg-white/70 shadow-xl dark:border-white/10 dark:bg-white/5">
      <CardHeader>
        <CardTitle className="flex items-center gap-2 text-lg"><NotebookPen className="h-5 w-5" /> Journal</CardTitle>
        <CardDescription>Capture reflection, clarity, and personal context.</CardDescription>
      </CardHeader>
      <CardContent className="space-y-4">
        <Input value={title} onChange={(e) => setTitle(e.target.value)} placeholder="Entry title" className="rounded-2xl" />
        <Textarea value={content} onChange={(e) => setContent(e.target.value)} placeholder="What are you noticing right now?" className="min-h-[100px] rounded-2xl" />
        <div className="flex flex-wrap gap-2">
          {(['Great', 'Good', 'Okay', 'Low'] as JournalEntry['mood'][]).map((m) => (
            <Button key={m} variant={mood === m ? 'default' : 'outline'} className="rounded-2xl" onClick={() => setMood(m)}>
              {m}
            </Button>
          ))}
          <Button
            className="ml-auto rounded-2xl"
            onClick={() => {
              if (!title.trim() && !content.trim()) return;
              setState((s) => ({
                ...s,
                journal: [{ id: uid(), title: title || 'Untitled entry', content, mood, date: todayISO() }, ...s.journal],
              }));
              setTitle('');
              setContent('');
            }}
          >
            Save entry
          </Button>
        </div>

        <div className="space-y-2">
          {entries.slice(0, 3).map((entry) => (
            <div key={entry.id} className="rounded-2xl border border-black/5 bg-white/60 p-4 dark:border-white/10 dark:bg-white/[0.03]">
              <div className="flex items-center justify-between gap-3">
                <div>
                  <div className="font-medium">{entry.title}</div>
                  <div className="text-sm text-zinc-500">{prettyDate(entry.date)} · {entry.mood}</div>
                </div>
                <Badge className="rounded-full">{entry.mood}</Badge>
              </div>
              <p className="mt-3 text-sm leading-6 text-zinc-600 dark:text-zinc-300">{entry.content}</p>
            </div>
          ))}
        </div>
      </CardContent>
    </Card>
  );
}

// ------------------------------------------------------------
// Page Editor
// ------------------------------------------------------------
function PageEditor({ page, updateActivePage }: { page: Page; updateActivePage: (updater: (page: Page) => Page) => void }) {
  return (
    <div className="grid gap-6 xl:grid-cols-[minmax(0,1fr)_300px]">
      <Card className="rounded-[30px] border-black/5 bg-white/70 shadow-2xl dark:border-white/10 dark:bg-white/5">
        <CardContent className="p-6 md:p-8">
          <input
            value={page.title}
            onChange={(e) => updateActivePage((p) => ({ ...p, title: e.target.value }))}
            className="mb-2 w-full bg-transparent text-4xl font-semibold tracking-tight outline-none placeholder:text-zinc-400"
            placeholder="Untitled"
          />
          <Textarea
            value={page.description}
            onChange={(e) => updateActivePage((p) => ({ ...p, description: e.target.value }))}
            className="mb-6 min-h-[72px] rounded-2xl border-black/5 bg-white/80 dark:border-white/10 dark:bg-white/[0.03]"
            placeholder="Write a short page description…"
          />

          <div className="space-y-2">
            {page.blocks.map((block, index) => (
              <BlockRow
                key={block.id}
                block={block}
                onChange={(updated) =>
                  updateActivePage((p) => ({
                    ...p,
                    blocks: p.blocks.map((b) => (b.id === block.id ? updated : b)),
                  }))
                }
                onDelete={() =>
                  updateActivePage((p) => ({
                    ...p,
                    blocks: p.blocks.filter((b) => b.id !== block.id),
                  }))
                }
                onMoveUp={() =>
                  updateActivePage((p) => {
                    if (index === 0) return p;
                    const next = [...p.blocks];
                    [next[index - 1], next[index]] = [next[index], next[index - 1]];
                    return { ...p, blocks: next };
                  })
                }
                onMoveDown={() =>
                  updateActivePage((p) => {
                    if (index === p.blocks.length - 1) return p;
                    const next = [...p.blocks];
                    [next[index], next[index + 1]] = [next[index + 1], next[index]];
                    return { ...p, blocks: next };
                  })
                }
              />
            ))}
          </div>
        </CardContent>
      </Card>

      <div className="space-y-4">
        <Card className="rounded-[28px] border-black/5 bg-white/70 shadow-xl dark:border-white/10 dark:bg-white/5">
          <CardHeader>
            <CardTitle className="text-lg">Block library</CardTitle>
            <CardDescription>Add and compose content like a lighter, calmer Notion.</CardDescription>
          </CardHeader>
          <CardContent className="grid gap-2">
            {blockTypeMeta.map((item) => (
              <Button
                key={item.type}
                variant="outline"
                className="justify-start rounded-2xl"
                onClick={() =>
                  updateActivePage((p) => ({
                    ...p,
                    blocks: [...p.blocks, { id: uid(), type: item.type, text: item.type === 'divider' ? '' : `${item.label}…`, checked: false, open: true }],
                  }))
                }
              >
                {item.icon}
                <span className="ml-2">{item.label}</span>
              </Button>
            ))}
          </CardContent>
        </Card>

        <Card className="rounded-[28px] border-black/5 bg-white/70 shadow-xl dark:border-white/10 dark:bg-white/5">
          <CardHeader>
            <CardTitle className="text-lg">Page tips</CardTitle>
          </CardHeader>
          <CardContent className="space-y-3 text-sm leading-6 text-zinc-600 dark:text-zinc-300">
            <p>Use headings to structure pages into clean sections.</p>
            <p>Add toggles for hidden details like notes, references, or brainstorms.</p>
            <p>Create separate pages for projects, journals, routines, and long-form planning.</p>
          </CardContent>
        </Card>
      </div>
    </div>
  );
}

function BlockRow({
  block,
  onChange,
  onDelete,
  onMoveUp,
  onMoveDown,
}: {
  block: Block;
  onChange: (block: Block) => void;
  onDelete: () => void;
  onMoveUp: () => void;
  onMoveDown: () => void;
}) {
  if (block.type === 'divider') {
    return (
      <div className="group flex items-center gap-2 rounded-2xl px-2 py-2">
        <div className="flex gap-1 opacity-0 transition group-hover:opacity-100">
          <button className="rounded-lg p-1 hover:bg-black/5 dark:hover:bg-white/10" onClick={onMoveUp}><ChevronUp /></button>
          <button className="rounded-lg p-1 hover:bg-black/5 dark:hover:bg-white/10" onClick={onMoveDown}><ChevronDownLite /></button>
        </div>
        <div className="h-px flex-1 bg-black/10 dark:bg-white/10" />
        <button className="rounded-lg p-1 opacity-0 transition hover:bg-black/5 group-hover:opacity-100 dark:hover:bg-white/10" onClick={onDelete}>
          <Trash2 className="h-4 w-4" />
        </button>
      </div>
    );
  }

  if (block.type === 'todo') {
    return (
      <div className="group flex items-start gap-3 rounded-2xl px-2 py-1 transition hover:bg-black/[0.03] dark:hover:bg-white/[0.03]">
        <div className="mt-2 flex items-center gap-1 opacity-0 transition group-hover:opacity-100">
          <button className="rounded-lg p-1 hover:bg-black/5 dark:hover:bg-white/10" onClick={onMoveUp}><ChevronUp /></button>
          <button className="rounded-lg p-1 hover:bg-black/5 dark:hover:bg-white/10" onClick={onMoveDown}><ChevronDownLite /></button>
        </div>
        <Checkbox checked={block.checked} onCheckedChange={(checked) => onChange({ ...block, checked: Boolean(checked) })} className="mt-3" />
        <input
          value={block.text}
          onChange={(e) => onChange({ ...block, text: e.target.value })}
          className={cn('w-full bg-transparent py-2 outline-none', block.checked && 'line-through text-zinc-400')}
          placeholder="To-do"
        />
        <button className="rounded-lg p-1 opacity-0 transition hover:bg-black/5 group-hover:opacity-100 dark:hover:bg-white/10" onClick={onDelete}>
          <Trash2 className="h-4 w-4" />
        </button>
      </div>
    );
  }

  if (block.type === 'toggle') {
    return (
      <div className="group rounded-2xl px-2 py-1 transition hover:bg-black/[0.03] dark:hover:bg-white/[0.03]">
        <div className="flex items-start gap-2">
          <div className="mt-2 flex items-center gap-1 opacity-0 transition group-hover:opacity-100">
            <button className="rounded-lg p-1 hover:bg-black/5 dark:hover:bg-white/10" onClick={onMoveUp}><ChevronUp /></button>
            <button className="rounded-lg p-1 hover:bg-black/5 dark:hover:bg-white/10" onClick={onMoveDown}><ChevronDownLite /></button>
          </div>
          <button className="mt-2 rounded-lg p-1 hover:bg-black/5 dark:hover:bg-white/10" onClick={() => onChange({ ...block, open: !block.open })}>
            {block.open ? <ChevronDown className="h-4 w-4" /> : <ChevronRight className="h-4 w-4" />}
          </button>
          <div className="flex-1">
            <input
              value={block.text}
              onChange={(e) => onChange({ ...block, text: e.target.value })}
              className="w-full bg-transparent py-2 font-medium outline-none"
              placeholder="Toggle title"
            />
            <AnimatePresence initial={false}>
              {block.open && (
                <motion.div
                  initial={{ opacity: 0, height: 0 }}
                  animate={{ opacity: 1, height: 'auto' }}
                  exit={{ opacity: 0, height: 0 }}
                  className="overflow-hidden pl-1 pr-4 text-sm text-zinc-500"
                >
                  Hidden content area — duplicate this block type later if you want nested toggles or richer children.
                </motion.div>
              )}
            </AnimatePresence>
          </div>
          <button className="rounded-lg p-1 opacity-0 transition hover:bg-black/5 group-hover:opacity-100 dark:hover:bg-white/10" onClick={onDelete}>
            <Trash2 className="h-4 w-4" />
          </button>
        </div>
      </div>
    );
  }

  const commonInput = (
    <input
      value={block.text}
      onChange={(e) => onChange({ ...block, text: e.target.value })}
      className={cn(
        'w-full bg-transparent outline-none',
        block.type === 'h1' && 'py-2 text-3xl font-semibold tracking-tight',
        block.type === 'h2' && 'py-2 text-2xl font-semibold tracking-tight',
        block.type === 'quote' && 'rounded-r-2xl border-l-2 border-zinc-300 py-2 pl-4 italic text-zinc-600 dark:border-zinc-700 dark:text-zinc-300',
        block.type === 'text' && 'py-2 leading-7'
      )}
      placeholder={block.type === 'text' ? 'Type something…' : 'Write here…'}
    />
  );

  return (
    <div className="group flex items-start gap-2 rounded-2xl px-2 py-1 transition hover:bg-black/[0.03] dark:hover:bg-white/[0.03]">
      <div className="mt-2 flex items-center gap-1 opacity-0 transition group-hover:opacity-100">
        <button className="rounded-lg p-1 hover:bg-black/5 dark:hover:bg-white/10" onClick={onMoveUp}><ChevronUp /></button>
        <button className="rounded-lg p-1 hover:bg-black/5 dark:hover:bg-white/10" onClick={onMoveDown}><ChevronDownLite /></button>
      </div>
      <div className="mt-2 text-zinc-400"><GripVertical className="h-4 w-4" /></div>
      <div className="flex-1">{commonInput}</div>
      <button className="rounded-lg p-1 opacity-0 transition hover:bg-black/5 group-hover:opacity-100 dark:hover:bg-white/10" onClick={onDelete}>
        <Trash2 className="h-4 w-4" />
      </button>
    </div>
  );
}

function ChevronUp() {
  return <ChevronRight className="h-4 w-4 rotate-[-90deg]" />;
}

function ChevronDownLite() {
  return <ChevronRight className="h-4 w-4 rotate-90" />;
}

// ------------------------------------------------------------
// Command Palette
// ------------------------------------------------------------
function CommandPalette({
  open,
  onOpenChange,
  pages,
  onSelectPage,
  onCreatePage,
}: {
  open: boolean;
  onOpenChange: (open: boolean) => void;
  pages: Page[];
  onSelectPage: (id: string) => void;
  onCreatePage: () => void;
}) {
  const [query, setQuery] = useState('');
  const inputRef = useRef<HTMLInputElement | null>(null);

  useEffect(() => {
    if (open) {
      setQuery('');
      setTimeout(() => inputRef.current?.focus(), 10);
    }
  }, [open]);

  const items = pages.filter((p) => p.title.toLowerCase().includes(query.toLowerCase()));

  return (
    <Dialog open={open} onOpenChange={onOpenChange}>
      <DialogContent className="overflow-hidden rounded-[28px] border-black/5 bg-white/90 p-0 shadow-2xl backdrop-blur-2xl dark:border-white/10 dark:bg-zinc-950/90 sm:max-w-xl">
        <div className="border-b border-black/5 p-3 dark:border-white/10">
          <div className="flex items-center gap-2 rounded-2xl border border-black/5 px-3 py-2 dark:border-white/10">
            <Search className="h-4 w-4 text-zinc-500" />
            <input
              ref={inputRef}
              value={query}
              onChange={(e) => setQuery(e.target.value)}
              className="w-full bg-transparent outline-none"
              placeholder="Search pages or create something new…"
            />
          </div>
        </div>

        <div className="max-h-[420px] overflow-y-auto p-3">
          <div className="mb-2 px-2 text-xs uppercase tracking-[0.2em] text-zinc-500">Pages</div>
          <div className="space-y-1">
            {items.map((page) => (
              <button
                key={page.id}
                className="flex w-full items-center gap-3 rounded-2xl px-3 py-2 text-left transition hover:bg-black/5 dark:hover:bg-white/10"
                onClick={() => {
                  onSelectPage(page.id);
                  onOpenChange(false);
                }}
              >
                <span>{pageIconMap[page.icon]}</span>
                <span className="flex-1">{page.title}</span>
                <span className="text-xs text-zinc-500">Open</span>
              </button>
            ))}
            <button
              className="flex w-full items-center gap-3 rounded-2xl px-3 py-2 text-left transition hover:bg-black/5 dark:hover:bg-white/10"
              onClick={() => {
                onCreatePage();
                onOpenChange(false);
              }}
            >
              <Plus className="h-4 w-4" />
              <span className="flex-1">Create new page</span>
              <span className="text-xs text-zinc-500">Enter</span>
            </button>
          </div>
        </div>
      </DialogContent>
    </Dialog>
  );
}

// ------------------------------------------------------------
// Widget Editor
// ------------------------------------------------------------
function WidgetEditorDialog({
  open,
  onOpenChange,
  widgets,
  setWidgets,
}: {
  open: boolean;
  onOpenChange: (open: boolean) => void;
  widgets: WidgetType[];
  setWidgets: (widgets: WidgetType[]) => void;
}) {
  const allWidgets: { id: WidgetType; title: string; description: string }[] = [
    { id: 'focus', title: 'Focus Score', description: 'Daily momentum overview' },
    { id: 'tasks', title: 'Tasks', description: 'Action list with priorities' },
    { id: 'agenda', title: 'Agenda', description: 'Today schedule snapshot' },
    { id: 'habits', title: 'Habits', description: 'Consistency tracker' },
    { id: 'goals', title: 'Goals', description: 'Long-term progress meter' },
    { id: 'journal', title: 'Journal', description: 'Reflection and context' },
  ];

  const toggleWidget = (id: WidgetType) => {
    if (widgets.includes(id)) {
      setWidgets(widgets.filter((w) => w !== id));
    } else {
      setWidgets([...widgets, id]);
    }
  };

  return (
    <Dialog open={open} onOpenChange={onOpenChange}>
      <DialogContent className="rounded-[28px] border-black/5 bg-white/90 shadow-2xl backdrop-blur-2xl dark:border-white/10 dark:bg-zinc-950/90 sm:max-w-2xl">
        <DialogHeader>
          <DialogTitle>Customize dashboard widgets</DialogTitle>
          <DialogDescription>Choose what appears on the home dashboard.</DialogDescription>
        </DialogHeader>
        <div className="grid gap-3 sm:grid-cols-2">
          {allWidgets.map((widget) => {
            const active = widgets.includes(widget.id);
            return (
              <button
                key={widget.id}
                onClick={() => toggleWidget(widget.id)}
                className={cn(
                  'rounded-3xl border p-4 text-left transition',
                  active
                    ? 'border-zinc-900 bg-zinc-900 text-white dark:border-white dark:bg-white dark:text-zinc-900'
                    : 'border-black/5 bg-white/60 hover:bg-white dark:border-white/10 dark:bg-white/[0.03] dark:hover:bg-white/[0.06]'
                )}
              >
                <div className="font-medium">{widget.title}</div>
                <div className={cn('mt-1 text-sm', active ? 'text-white/80 dark:text-zinc-700' : 'text-zinc-500')}>{widget.description}</div>
              </button>
            );
          })}
        </div>
        <DialogFooter>
          <Button className="rounded-2xl" onClick={() => onOpenChange(false)}>Done</Button>
        </DialogFooter>
      </DialogContent>
    </Dialog>
  );
}
