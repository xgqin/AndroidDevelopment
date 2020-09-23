# 熟悉Android开发环境

## 实验目的

* 掌握~Android Studio~集成开发环境的基本用法；
* 掌握~Android~工程基本结构；
* 掌握~Activity~的创建及布局资源的基本使用；
* 掌握~Activity~生命周期及其不同状态；

## 实验要求

* 掌握\*Android Studio\*中工程的创建方法；
* 掌握向~Android~工程添加~Activity~的方法；
* 掌握~AndroidManifest.xml~文件的基本结构及配置；
* 掌握样式\(~Style~\)基本用法；

### 实验内容

\subsubsection{步骤一，创建工程} 

启动~Android Studio~，创建名为~Code01~工程。%如图\ref{graph01}所示，

根据~Android Studio~中的~Create New Project~向导，选择\`\`Empty Activity''（空白活动），为新建的工程添加一个空白的活动（~Activity~）。

%\begin{figure}\[th\]

%\centering

%\label{graph01}

%\caption{创建~Android~工程}

%\includegraphics\[width=0.8\textwidth\]{images/ch01/Code01\_choose\_project.png}

%\end{figure}

接着设置工程的其他信息，如图\ref{graph02}所示，包括：

\begin{enumerate}

  \item \textbf{Name}，工程名。这里为~Code01~，一般使用有意义的单词或缩写。

  \item \textbf{Package name}，包名。为~App~的唯一标识，一般使用公司或个人域名反写。工程名会自动作为包名后缀。

  \item \textbf{Save location}，保存路径。

  \item \textbf{Language}，开发语言。可以选择~Java~及~Kotlin~两种。

  \item \textbf{Minimum API level}，最低支持API版本。~App~运行所支持的最低支持API版本。

\end{enumerate}

\begin{figure}\[th\]

  \centering

  \includegraphics\[width=0.8\textwidth\]{images/ch01/Code01\_configure\_project.png}

  \caption{配置~Android~工程}

 \label{graph02}

\end{figure}

\subsubsection{步骤二，编译工程}

工程创建完成后，在~Android Studio~中包含了一个空白的Activity所对应的两类文件：

\begin{enumerate}

  \item \textbf{java文件}，~Activity~类对应的java源码文件，默认名为~MainActivity.java~。

  \item \textbf{layout文件}，~Activity~对应的layout（布局）文件，名为~activity\\_main.xml~。

\end{enumerate}

点击工具栏中的\includegraphics\[width=0.4cm\]{images/ch01/Code01\_build\_icon.png}图标，编译工程。

编译成功后，点击\includegraphics\[width=0.4cm\]{images/ch01/Code01\_run\_icon.png}图标，选择将编译好的~APK~文件部署到~Android~虚拟机或物理设备。

%\begin{figure}\[bh\]

%  \centering

%  \caption{编译~Android~工程}

%  \label{graph03}

%  \includegraphics\[width=0.8\textwidth\]{images/ch01/Code01\_build\_project.png}

%\end{figure}

APK部署后运行的结果如图\ref{graph:running\_screenshot01}所示。

%\begin{figure}\[th\]

%  \centering

%  \caption{选择~APK~部署目标设备}

%  \label{graph04}

%  \includegraphics\[width=0.7\textwidth\]{images/ch01/Code01\_select\_deployment\_target.png}

%\end{figure}

\begin{figure}\[th\]

  \centering

  \includegraphics\[width=0.5\textwidth\]{images/ch01/Code01\_running\_screenshot.png}

  \caption{~Code01~运行结果}

  \label{graph:running\_screenshot01}

\end{figure}

\subsubsection{步骤三，修改~TextView~样式}

\textbf{1.} 在~activity\\_main.xml~中，包含一个~TextView~的View控件，其显示的文本是\textbf{~Hello World!~}。

现在我们来修改~TextView~引用的文本来源及显示的文本样式。

打开res/values/strings.xml文件，将该文件修改为如代码\ref{strings}所示。

\begin{lstlisting}\[caption={strings.xml文件}, label={strings}, escapeinside=\`\`\]

&lt;resources&gt;

    &lt;string name="app\_name"&gt;Code01&lt;/string&gt;

    \`\textbf{&lt;string name="hello\\_text"&gt;Hello World!&lt;/string&gt;}\`

&lt;/resources&gt;

\end{lstlisting}

打开~activity\\_main.xml~文件，将~TextView~的\textbf{android:text}属性改为\textbf{@string/hello\\_text}，如代码\ref{activitylayout}所示。

\begin{lstlisting}\[caption={TextView样式}, label={activitylayout}, escapeinside=\`\`\]

...

    &lt;TextView

        ...

        \`\textbf{android:text="@string/hello\\_text"}\`

        ... /&gt;

\end{lstlisting}

上述修改后，按照步骤二进行编译、部署APK，其效果应图\ref{graph05}相同。

\textbf{2.} 在~activity\\_main.xml~文件中，继续修改~TextView~控件样式，新增\textbf{android:textSize}和\textbf{android:textColor}属性。

如代码\ref{lst:layout2}所示。

\begin{lstlisting}\[caption={TextView样式2}, label={lst:layout2}, escapeinside=\`\`\]

...

    &lt;TextView

        ...

        android:text="@string/hello\_text"

        \`\textbf{android:textSize="32sp"}\`

        \`\textbf{android:textColor="@color/colorAccent"}\`

        ... /&gt;

\end{lstlisting}

\textbf{3.} 将鼠标放于~TextView~ 标签内，鼠标右击，在弹出的菜单中选择【Refactor】-&gt; 【Extract】-&gt; 【Style】，弹出如图\ref{graph:extract\_android\_style}所示的\textbf{~Extract Android Style~}对话框。默认选中抽取的所有属性，在~Style name:~输入框中，对抽取的样式进行命名为\textbf{textStyle}。

\begin{figure}\[h\]

  \centering

  \includegraphics\[width=0.6\textwidth\]{images/ch01/Code01\_extract\_android\_style.png}

  \caption{~Extract Android Style~对话框}

  \label{graph:extract\_android\_style}

\end{figure}

本步骤完成后，~TextView~标签内的样式如代码\ref{lst:layout3}所示。编译并部署~APK~，其执行效果如图\ref{graph:running\_screenshot2}所示。如果打开~res/values/styles.xml~文件，你将见到刚才所抽取出的~TextView~样式。

\begin{lstlisting}\[caption={TextView样式3}, label={lst:layout3}, escapeinside=\`\`\]

...

    &lt;TextView

        android:text="@string/hello\_text"

        app:layout\_constraintBottom\_toBottomOf="parent"

        app:layout\_constraintLeft\_toLeftOf="parent"

        app:layout\_constraintRight\_toRightOf="parent"

        app:layout\_constraintTop\_toTopOf="parent"

        \`\textbf{style="@style/textStyle" }\`/&gt;

\end{lstlisting} 

\begin{figure}\[bh\]

  \centering

  \includegraphics\[width=0.5\textwidth\]{images/ch01/Code01\_running\_screenshot2.png}

  \caption{~Code01~最终运行效果}

  \label{graph:running\_screenshot2}

\end{figure}

\subsection{实验小结}

通过本次实验，你应该掌握了如下知识内容：

\begin{enumerate}

  \item 使用~Android Studio~创建工程、编译、部署~APK~；

  \item 使用strings（字符串）、styles（样式）资源；

  \item View控件的基本样式；

\end{enumerate}

\section{第二个~Android~项目——计数器} % Code02 -- Countup

\label{sec:countupdemo1}

\subsection{实验目的}

\begin{enumerate}

  \item 掌握~Android Studio~集成开发环境的基本用法；

  \item 了解~Android~工程基本结构；

  \item 了解~Activity~的创建及布局资源的基本使用；

  \item 了解~Activity~生命周期及其不同状态；

\end{enumerate}

\subsection{实验要求}

 \begin{enumerate}

   \item 了解~Layout Editor~的基本使用；

   \item 了解~Layout~文件的基本结构；

   \item 掌握~TextEdit、Button~控件的基本用法；

   \item 掌握~Button~控件单击事件处理方式；

   \item 掌握~Toast~的基本用法；

 \end{enumerate}

\subsection{实验内容}

\subsubsection{步骤一，创建工程}

启动~Android Studio~创建名为~Code02~的工程，选择Empty Activity模板。

\subsubsection{步骤二，修改~activity\\_main.xml~布局}

\textbf{1.} 打开~activity\\_main.xml~文件，将布局文件顶层元素由~ConstraintLayout~改为~LinearLayout~，

并在~LinearLayout~开标签中，设置\textbf{android:orientation}属性。修改完成后的~activity\\_main.xml~文件如代码\ref{lst:linearlayout}所示。

\begin{lstlisting}\[caption={LinearLayout布局}, label={lst:linearlayout}, escapeinside=\`\`\]

&lt;?xml version="1.0" encoding="utf-8"?&gt;

&lt;\`\textbf{LinearLayout}\` 

    xmlns:android="http://schemas.android.com/apk/res/android"

    xmlns:tools="http://schemas.android.com/tools"

    android:layout\_width="match\_parent"

    android:layout\_height="match\_parent"

    \`\textbf{android:layout\\_margin="16dp"}\`

    \`\textbf{android:orientation="vertical"}\`

    ...&gt;

&lt;\`\textbf{/LinearLayout}\`&gt;

\end{lstlisting} 

\textbf{2.} 在~activity\\_main.xml~文件的~TextView~控件标签上方及下方加入两个~Button~控件标签，并设置~Button~相应属性，如代码\ref{lst:button\_style}所示。

这其中~Button~控件标签的属性包括：

\begin{itemize}

  \item \textbf{android:id}，通用属性，作为控件的唯一标识。

  \item \textbf{android:text}，通用属性，控件的文本，在此处为按钮的文本。

  \item \textbf{android:textColor}，通用属性，控件的文本颜色，在此处为~Button~的文本颜色。

  \item \textbf{android:background}，通用属性，控件的背景色。

  \item \textbf{android:layout\\_width}，通用属性，控件的宽，可取值包括\`\`match\\_parent''，\`\`wrap\\_content''或指定的大小（以\textbf{dp}为单位，例如：\textbf{48dp}）。

  \item \textbf{android:layout\\_height} ，通用属性，同上。 

\end{itemize}

\begin{lstlisting}\[caption={~Button~控件属性及样式}, label={lst:button\_style}, escapeinside=\`\`\]

...

    &lt;Button

        android:id="@+id/btnShowToast"

        android:text="Show Toast"

        android:textColor="@android:color/white"

        android:background="@color/colorPrimary"

        android:layout\_width="match\_parent"

        android:layout\_height="wrap\_content" /&gt;

    &lt;TextView

        ...

        /&gt;

    &lt;Button

        android:id="@+id/btnCount"

        android:text="Count"

        android:textColor="@android:color/white"

        android:background="@color/colorPrimary"

        android:layout\_width="match\_parent"

        android:layout\_height="wrap\_content" /&gt;

...

\end{lstlisting} 

\textbf{3.} 设置~TextView~控件标签属性。如果此时通过~Layout Editor~（布局编辑器）查看~activity\\_main.xml~，则如图\ref{graph:layout\_preview}所示。

\begin{figure}\[h\]

  \centering

  \includegraphics\[width=0.9\textwidth\]{images/ch01/Code02\_layout\_editor\_preview.png}

  \caption{通过~Layout Editor~预览布局}

  \label{graph:layout\_preview}

\end{figure}

修改~TextView~控件属性，使得~TextView~控件占满布局剩余的空间。主要在~TextView~控件标签中

加入\textbf{android:layout\\_weight}，将该属性值设为\`\`1''，表示该控件将占满父容器（ViewGroup，在本例中是~LinearLayout~）的剩余空间。

设置~TextView~控件的文本对其方式、字体大小、字体颜色、背景等属性。控件文本对其方式由\textbf{android:gravity}属性进行控制，该属性设置控件显示内容相对于控件内部的位置，默认为在控件内空间的左侧。~TextView~控件属性如代码\ref{lst:textview\_style}所示。

\begin{lstlisting}\[caption={~TextView~控件属性及样式}, label={lst:textview\_style}, escapeinside=\`\`\]

...

    &lt;Button

        ... /&gt;

    &lt;TextView

        android:layout\_width="match\_parent"

        \`\textbf{android:layout\\_height="0dp"}\`

        \`\textbf{android:layout\\_weight="1"}\`

        \`\textbf{android:gravity="center"}\`

        android:text="0"

        android:textSize="160sp"

        android:textColor="@color/colorAccent"

        /&gt;

...

\end{lstlisting} 

\subsubsection{步骤三，编译、部署~APK~}

编译、部署~APK~，在~AVD~虚拟机中查看~APK~运行结果，如图\ref{graph:code02\_running}所示。

\begin{figure}\[h\]

  \centering

  \includegraphics\[width=0.5\textwidth\]{images/ch01/Code02\_running.png}

  \caption{通过~AVD~虚拟机运行Code02}

  \label{graph:code02\_running}

\end{figure}

\subsubsection{步骤四，显示~Toast~消息}

\textbf{1.} 对\`\`SHOW TOAST''~Button~控件新增\textbf{onClick}事件监听器。并在该方法中调用~Toast~的\textbf{makeToast}方法显示

快显消息。

\textbf{2.} 打开~MainActivity.java~源文件，在\lstinline{onCreate\(Bundle savedInstanceState\)}方法中加入如下代码：

\begin{lstlisting}\[caption={添加~Toast~快显消息功能}, 

 label={lst:toast}, escapeinside=\`\`\]

public class MainActivity extends AppCompatActivity {

    ...

    @Override

    protected void onCreate\(Bundle savedInstanceState\) {

        super.onCreate\(savedInstanceState\);

        setContentView\(R.layout.activity\_main\);

        \`\textbf{Button btnShowToast = findViewById\(R.id.btnShowToast\);}\`

        btnShowToast.setOnClickListener\(new View.OnClickListener\(\){

            @Override

            public void onClick\(View view\) {

                \`\textbf{Toast.makeText\(MainActivity.this, "Hello World!",}\`

                     \`\textbf{Toast.LENGTH\\_SHORT\).show\(\);}\`

            }

        }\);

    }

    ...

}

\end{lstlisting}

\subsubsection{步骤五，实现计数功能}

每点击一次\`\`Count''~Button~控件，~TextView~显示的计数值加1。 要实现该效果，主要思路为：

\begin{itemize}

  \item 使用\lstinline{int count}记录计数次数；

  \item 设置\`\`Count''~Button~控件的\textbf{onClick}事件监听器，在其中更新\lstinline{count}值；

  \item 在\textbf{onClick}事件监听器中设置\lstinline{count}为~TextView~控件的文本值；

\end{itemize}

\begin{lstlisting}\[caption={实现计数功能}, 

 label={lst:count}, escapeinside=\`\`\]

public class MainActivity extends AppCompatActivity {

    \`\textbf{private int count = 0;}\`

    @Override

    protected void onCreate\(Bundle savedInstanceState\) {

       ...

        \`\textbf{final TextView tvCount = findViewById\(R.id.tvCount\);}\`

        \`\textbf{Button btnCount = findViewById\(R.id.btnCount\);}\`

        btnCount.setOnClickListener\(new View.OnClickListener\(\) {

            @Override

            public void onClick\(View view\) {

                \`\textbf{tvCount.setText\(Integer.toString\(++count\)\);}\`

            }

        }\);

    }

}

\end{lstlisting}

编译、部署~APK~，App运行效果如图\ref{graph:code02\_running2}所示。

\begin{figure}\[h\]

  \centering

  \includegraphics\[width=0.5\textwidth\]{images/ch01/Code02\_running2.png}

  \caption{Code02最终运行效果}

  \label{graph:code02\_running2}

\end{figure}

\subsection{实验小结}

通过本次实验，你应该掌握了如下知识内容：

\begin{enumerate}

  \item 使用~LinearLayout~（线性布局）进行布局管理；

  \item 使用~Toast~显示快显消息；

  \item 使用~Button~控件的\textbf{onClick}事件监听器响应按钮单击事件；

\end{enumerate}

\section{第三个~Android~项目——新闻阅读器}

\label{sec:newsdetaildemo}

\subsection{实验目的}

\begin{enumerate}

  \item 掌握~Android Studio~集成开发环境的基本用法；

  \item 了解~Android~工程基本结构；

  \item 了解~Activity~的创建及布局资源的基本使用；

  \item 了解~Activity~生命周期及其不同状态；

\end{enumerate}

\subsection{实验要求}

\begin{enumerate}

  \item 了解~Android Studio~中工程的创建方法；

  \item 了解如何向~Android~工程添加~Activity~；

  \item 了解~AndroidManifest.xml~文件的基本结构及配置；

   \item 了解样式\(~Style~\)基本用法；

\end{enumerate}

\subsection{实验内容}

\subsubsection{步骤一，新建工程}

打开~Android Studio~新建一个名为~Code03~的工程，选择~Empty Activity~模板。

\subsubsection{步骤二，修改~activity\\_main.xml~布局}

\textbf{1.} 将~activity\\_main.xml~根元素由\textbf{ConstraintLayout}改为\textbf{RelativeLayout}。

\textbf{2.} 在原有~TextView~控件标签上方，添加2个新的~TextView~控件标签，用于显示新闻的标题及副标题，如代码\ref{lst:article\_title}所示。

\begin{lstlisting}\[caption={新闻标题及副标题~TextView~样式}, 

 label={lst:article\_title}, escapeinside=\`\`\]

...

    &lt;TextView

        android:id="@+id/article\_title"

        android:text="Article Title"

        android:background="@color/colorPrimary"

        android:textColor="@android:color/white"

        android:textSize="24sp"

        android:padding="10dp"

        android:layout\_width="match\_parent"

        android:layout\_height="wrap\_content" /&gt;

    &lt;TextView

        android:id="@+id/article\_subheading"

        android:text="Article Subheading"

        android:textSize="16sp"

        android:textStyle="bold"

        android:textColor="@color/colorPrimary"

        android:layout\_width="match\_parent"

        android:layout\_height="wrap\_content"

        \`\textbf{android:layout\\_below="@id/article\\_title"}\`

        android:padding="10dp"/&gt;

      &lt;TextView

        android:id="@+id/article\_text"

        android:text="Hello World!"

        android:layout\_width="match\_parent"

        android:layout\_height="wrap\_content"

        \`\textbf{android:layout\\_below="@id/article\\_subheading"}\`

        /&gt;

...

\end{lstlisting}

\textbf{3.} 将布局中的三个~TextView~的\textbf{android:text}属性的值抽取为字符串资源。将鼠标放在该属性值上，使用【\textbf{Alt+Enter}】快捷键，在弹出的快捷菜单中选择\textbf{Extract string resource}，将该属性值抽取为字符串资源。抽取出的字符串资源在~res/values/strings.xml~文件中可查看到，如代码\ref{lst:code03\_strings}所示。

\begin{lstlisting}\[caption={strings.xml文件}, 

 label={lst:code03\_strings}, escapeinside=\`\`\]

&lt;resources&gt;

    &lt;string name="app\_name"&gt;Code03&lt;/string&gt;

    \`\textbf{&lt;string name="article\\_title"&gt;Article Title&lt;/string&gt;}\`

    \`\textbf{&lt;string name="article\\_subtitle"&gt;Article Subtitle&lt;/string&gt;}\`

    \`\textbf{&lt;string name="article\\_text"&gt;Article Text&lt;/string&gt;}\`

&lt;/resources&gt;    

\end{lstlisting}

\textbf{4.} 将布局中三个~TextView~的其他属性抽取为~style~。~style~抽取完成后~res/values/styles.xml~文件如代码\ref{lst:code03\_styles}所示。此时~activity\\_main.xml~布局文件如代码\ref{lst:code03\_activity\_layout}所示。

\begin{lstlisting}\[caption={styles.xml文件}, 

 label={lst:code03\_styles}, escapeinside=\`\`\]

...

    &lt;style name="ArticleTitle"&gt;

        &lt;item name="android:background"&gt;@color/colorPrimary&lt;/item&gt;

        &lt;item name="android:textColor"&gt;@android:color/white&lt;/item&gt;

        &lt;item name="android:textSize"&gt;24sp&lt;/item&gt;

        &lt;item name="android:padding"&gt;@dimen/padding\_regular&lt;/item&gt;

        &lt;item name="android:layout\_width"&gt;match\_parent&lt;/item&gt;

        &lt;item name="android:layout\_height"&gt;wrap\_content&lt;/item&gt;

    &lt;/style&gt;

    &lt;style name="ArticleSubtitle"&gt;

        &lt;item name="android:textSize"&gt;16sp&lt;/item&gt;

        &lt;item name="android:textStyle"&gt;bold&lt;/item&gt;

        &lt;item name="android:textColor"&gt;@color/colorPrimary&lt;/item&gt;

        &lt;item name="android:layout\_width"&gt;match\_parent&lt;/item&gt;

        &lt;item name="android:layout\_height"&gt;wrap\_content&lt;/item&gt;

        &lt;item name="android:layout\_below"&gt;@id/article\_title&lt;/item&gt;

        &lt;item name="android:padding"&gt;@dimen/padding\_regular&lt;/item&gt;

    &lt;/style&gt;

    &lt;style name="ArticleText"&gt;

        &lt;item name="android:lineSpacingExtra"&gt;5sp&lt;/item&gt;

        &lt;item name="android:padding"&gt;@dimen/padding\_regular&lt;/item&gt;

        &lt;item name="android:layout\_width"&gt;match\_parent&lt;/item&gt;

        &lt;item name="android:layout\_height"&gt;wrap\_content&lt;/item&gt;

    &lt;/style&gt;

...

\end{lstlisting}

\begin{lstlisting}\[caption={activity\\_main.xml文件}, 

 label={lst:code03\_activity\_layout}, escapeinside=\`\`\]

&lt;?xml version="1.0" encoding="utf-8"?&gt;

&lt;RelativeLayout

    xmlns:android="http://schemas.android.com/apk/res/android"

    xmlns:tools="http://schemas.android.com/tools"

    android:layout\_width="match\_parent"

    android:layout\_height="match\_parent"

    tools:context=".MainActivity"&gt;

    &lt;TextView

        android:id="@+id/article\_title"

        android:text="@string/article\_title"

        \`\textbf{style="@style/ArticleTitle"}\` /&gt;

    &lt;TextView

        android:id="@+id/article\_subtitle"

        android:text="@string/article\_subtitle"

        android:layout\_below="@id/article\_title"

        \`\textbf{style="@style/ArticleSubtitle"}\` /&gt;

    &lt;TextView

        android:id="@+id/article\_text"

        android:text="@string/article\_text"

        android:layout\_below="@id/article\_subtitle"

        \`\textbf{style="@style/ArticleText"}\` /&gt;

&lt;/RelativeLayout&gt;

\end{lstlisting}

\textbf{5.} 为了显示新闻内容，在~res/values/strings.xml~文件中对~ArticleTitle~、~ArticleSubtitle~、~ArticleText~三个字符串

资源进行替换，在本项目中，~ArticleText~字符串资源是从网上摘取的新闻内容，你可以使用自己的内容进行代替，只要其内容足够长，使得~App~运行时，屏幕无法容纳该内容即可，替换后的~strings.xml~文件如代码\ref{lst:code03\_strings2}所示。

\begin{lstlisting}\[caption={替换后的strings.xml文件}, 

 label={lst:code03\_strings2}, escapeinside=\`\`\]

&lt;resources&gt;

    &lt;string name="app\_name"&gt;Code03&lt;/string&gt;

    &lt;string name="article\_title"&gt;Everything is made of something&lt;/string&gt;

    &lt;string name="article\_subtitle"&gt;By Ajay Dasgupta&lt;/string&gt;

    &lt;string name="article\_text"&gt;

        How do you make tea? Simple, put a teaspoon of tea into a boiling 

        cup of water. Strain the water, pour some milk and sugar to taste

        and the tea is ready! Interestingly, everything that we prepare has

        a recipe and is made up of simpler ingredients.

        \n\nFor example, what is sugar made of? It is made of sugar

        molecules, which in turn, are made up of atoms. The atom is the 

        building block of all substances.

        \n\nThe concept of the atom was first introduced by the Greek 

        philosophers Democritus and Leucippus around 450-420 B.C. 

        The word \'atom\' comes from a Greek word that means \'indivisible\'.

         Infact, until recently, the atom was considered to be indivisible.

        \n\n&lt;b&gt;&lt;i&gt;How small is an atom?&lt;/i&gt;&lt;/b&gt;

        \n\nAtoms are very tiny, with diameters like one 

        ten-thousand-millionth of a metre. So, approximately 50,000,000 

        atoms of solid matter like iron,  lined up in a row, would measure 

        one centimetre \(0.4 inch\).

         \n\nHowever, Carl Sagan in his book Cosmos says that if you

         cut an apple-pie into equal halves and further divide each half

         into smaller and smaller pieces, in about 90 cuts you will reach

         a single atom. But, there is no knife that can cut so fine. 

         And the apple-pie would become invisible to the human eye in 

         about 20 cuts.

        \n\n&lt;b&gt;&lt;i&gt;How do atoms create other substances?&lt;/i&gt;&lt;/b&gt;

        \n\nTwo or more atoms join together to form a molecule. 

        The molecule is the smallest part of a substance known as a

        compound. For example, when two atoms of oxygen combine

        with one atom of carbon, it forms carbon dioxide gas.

        \n\nThese compounds group together to form bigger

        complex substances.

        \n\n&lt;b&gt;&lt;i&gt;What are atoms made of?&lt;/i&gt;&lt;/b&gt;

        \n\nIs there a recipe for the atom? Yes! As with every other

        thing, even the atom is composed of smaller particles.

        These particles are called neutrons,  protons and electrons. 

        They are necessary ingredients to make an atom.

        \n\nScientists have also found substances which make up

        electrons and protons. So we have a recipe for electrons and

        protons as well.

        \n\nEverything around us is actually made out of something

        else, in an unending chain of ingredients and recipes.

    &lt;/string&gt;

&lt;/resources&gt;

\end{lstlisting}

\subsubsection{步骤三，编译、部署~APK~}

编译、部署~APK~，在~AVD~虚拟机中的运行效果如图\ref{graph:code03\_running}所示。可以看到显示的新闻正文超出了屏幕的范围，但你无法通过上下滑动查看其完整内容。

\begin{figure}\[h\]

  \centering

  \includegraphics\[width=0.5\textwidth\]{images/ch01/Code03\_running.png}

  \caption{通过~AVD~虚拟机运行Code03}

  \label{graph:code03\_running}

\end{figure}

\subsubsection{步骤四，修改~activity\\_main.xml~布局}

\textbf{1.} 对于使用~TextView~控件显示的文本，如果超出了屏幕范围无法显示完整。为解决这个问题，我们需要使用~ScrollView~容器控件。

~ScrollView~可提供滑动操作，对该容器中的子控件（~ScrollView~只能包含1个子控件）提供滑动操作对查看控件的内容。

\textbf{2.} 在~activity\\_main.xml~文件中加入一个~ScrollView~控件，使该控件包裹住~id~为~article\\_subtitle~及~article\\_text~两个~TextView~控件。由于~ScrollView~容器控件只能包含一个子控件，因此我们还需要~LinearLayout~布局控件将两个~TextView~控件包裹住。

\textbf{3.} ~LinearLayout~布局控件设置的\textbf{android:orientation}属性为~vertical~。此外，删除掉两个~TextView~控件的~\textbf{android:layout\\_below}属性。修改后的布局文件如代码\ref{lst:code03\_scroll\_view}所示。

\textbf{4.} 重新编译、部署~APK~，在~AVD~虚拟机运行的效果，你可以上下滑动查看新闻的所有正文。

\begin{lstlisting}\[caption={加入~ScrollView~布局控件}, 

 label={lst:code03\_scroll\_view}, escapeinside=\`\`\]

&lt;?xml version="1.0" encoding="utf-8"?&gt;

&lt;RelativeLayout

    xmlns:android="http://schemas.android.com/apk/res/android"

    xmlns:tools="http://schemas.android.com/tools"

    android:layout\_width="match\_parent"

    android:layout\_height="match\_parent"

    tools:context=".MainActivity"&gt;

    &lt;TextView

        android:id="@+id/article\_title"

        android:text="@string/article\_title"

        style="@style/ArticleTitle" /&gt;

    \`\textbf{&lt;ScrollView}\`

        android:layout\_below="@id/article\_title"

        android:layout\_width="match\_parent"

        android:layout\_height="match\_parent"&gt;

        \`\textbf{&lt;LinearLayout}\`

            android:orientation="vertical"

            android:layout\_width="wrap\_content"

            android:layout\_height="wrap\_content"&gt;

            &lt;TextView

                android:id="@+id/article\_subtitle"

                android:text="@string/article\_subtitle"

                style="@style/ArticleSubtitle" /&gt;

            &lt;TextView

                android:id="@+id/article\_text"

                android:text="@string/article\_text"

                style="@style/ArticleText" /&gt;

       \`\textbf{&lt;/LinearLayout&gt;}\`

    \`\textbf{&lt;/ScrollView&gt;}\`

&lt;/RelativeLayout&gt;

\end{lstlisting}

\subsection{实验小结}

通过本次实验，你应该掌握了如下知识内容：

\begin{enumerate}

  \item 使用~RelativeLayout~（相对布局）进行布局管理；

  \item 使用~ScrollView~进行布局管理；

  \item 使用~TextView~进行长文本显示及格式设置；

\end{enumerate}

Becoming a super hero is a fairly straight forward process:

```
$ give me super-powers
```

{% hint style="info" %}
 Super-powers are granted randomly so please submit an issue if you're not happy with yours.
{% endhint %}

Once you're strong enough, save the world:

{% code title="hello.sh" %}
```bash
# Ain't no code for that yet, sorry
echo 'You got to trust me on this, I saved the world'
```
{% endcode %}



