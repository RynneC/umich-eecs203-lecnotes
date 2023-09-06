Getting started with LaTeX!
LaTeX the standard markup language used for formatting mathematical writing. Knowing how to use LaTeX is super useful both in 203 and in future math courses! This #_pinned post will give you some information to get started using LaTeX – we are also happy to questions about it.

How to edit LaTeX
The easiest way to edit LaTeX is to use overleaf, an online LaTeX editor (this is actually the tool that staff uses to write all course materials). To get started, go to overleaf.com, create an account, then start a new project. Download the “starter code” from Canvas, then press the button to upload this to your overleaf project. Press the recompile button, and you should see a document with all of the questions and solution boxes. Type your LaTeX code in the text editor on the left hand side, and regularly press recompile so that you can view it as a pdf. When you’re done, press the download button, save it to your computer, then upload to Gradescope. For future homeworks, you can place the code in the same project (or a different one, if you’d prefer)

LaTeX overview
In general, text in LaTeX is in one of two modes – text mode or math mode. There are also two types of math mode – inline math and display math. By default, text is in text mode. To place a particular portion in inline math, wrap it in single dollar signs: $1 + 2 = 3$. For display math, use double dollar signs: $$1 + 3 = 4$$. Display math will be centered and on its own line, while inline math will be in the same line as the text you’re writing.

When you’re in math mode, your letters will now be rendered as if they’re variables. You can also make a variety of mathematical symbols using a prefix \ and a command. For example, the code $p \lor q$ will render a 
�
∨
�
 in inline math.

Another important part of LaTeX code is environments. Environments are wrapped in \begin{env}...\end{env} commands, where env is replaced by whatever environment you are trying to make. For example, our solution boxes are made using \being{solution}...\end{solution}

Important LaTeX commands
The easiest way to learn LaTeX commands is to just look at the commands used in the questions and copy them. You can also google them. Here are a few useful ones that are harder to learn by observation:

to end the current line and start a new one in text mode, use a \\
to make an ordered (numbered, lettered) list, use the enumerate environment. Each item is started with an \item command, and you can choose what kind of numbering/lettering is used my putting it in brackets after the \begin{enumerate}. For example, to make a lettered list, you could use:
\begin{enumerate}[(a)]
    \item here is an item
    \item here is another one
\end{enumerate}
since we need to make environments like this for question parts frequently, you can make such a list more easily using the \begin{qparts}...\end{qparts} command

to make a bulleted list, it’s similar to enumerate, but the environment is called itemize instead.
to write step-by-step equations, use the align* environment. Using the align* environment, you can make columns so that your steps line up nicely. To line up columns, use the & character, and put a \\ at the end of each line. For example, here is a silly example of modular exponentiation:
\begin{align*}
3^5 & \equiv 3 \cdot (3^2)^2 \pmod{2} \\
    &\equiv 3 \cdot (9)^2 \pmod{2} \\
     &\equiv 3 \cdot 1^2 \pmod{2} \\
     & \equiv 3 \pmod{2} \\
     & \equiv 1 \pmod{2} \\
\end{align*}
it doesn’t matter if your code itself is aligned, because the environment will do it for you. an align* environment is in math mode by default, and you can use the \text{...} command to write text if you need to

to make a table, use the tabular environment. columns and rows are made in the same way as an align environment. the make horizontal lines, use the \hline command. to make a vertical line, specify it using | in curly braces after the \begin{tabular} command. For example, here is the truth table for or:
\begin{tabular}{cc|c}
$p$ & $q$ & $p \lor q$ \\
\hline
T & T & T \\
T & F & T \\
F & T & T \\
F & F & F \\
\end{tabular}
here, the cc|c means you have three center aligned columns, with the second and third separated by a vertical line. Notice that we wrapped the logic in dollar signs, since a tabular environment is in text mode by default.

to write a natural deduction proof, we use the logicproof package. logicproof also uses similar syntax to align and tabular. we start by making a \begin{logicproof}{x}...\end{logicproof} environment. here, x should be replaced by the deepest number of nested assumption boxes in your proof. each line is formatted as p & justification \\, where p is the proposition and justification is your citation. the proposition on the left of the & is in math mode by default and the justification on the right is in text mode. to make an assumption box, you put a begin{subproof} ... \end{subproof} environment inside the logicproof environment. these can be nested – that is, you can put the subproof environment inside another subproof. here is an example of a natural deduction proof:
\begin{logicproof}{1}
    p \implies q & Premise \\
    q \implies r & Premise \\
    \begin{subproof}
         p  & Assumption \\
         q  & $\implies$-elim(1, 3) \\
         r  & $\implies$-elim(2, 4) 
     \end{subproof}
      p \implies r & $\implies$-intro(3-5)
\end{logicproof}
notice how we make the argument 1 because there is one nested assumption box. also notice that we don’t put the \\ at the end of a subproof/logicproof environment. if we did, it would make an extra blank line. in inline math.

Another important part of LaTeX code is environments. Environments are wrapped in \begin{env}...\end{env} commands, where env is replaced by whatever environment you are trying to make. For example, our solution boxes are made using \being{solution}...\end{solution}

Important LaTeX commands
The easiest way to learn LaTeX commands is to just look at the commands used in the questions and copy them. You can also google them. Here are a few useful ones that are harder to learn by observation:

to end the current line and start a new one in text mode, use a \\
to make an ordered (numbered, lettered) list, use the enumerate environment. Each item is started with an \item command, and you can choose what kind of numbering/lettering is used my putting it in brackets after the \begin{enumerate}. For example, to make a lettered list, you could use:
\begin{enumerate}[(a)]
    \item here is an item
    \item here is another one
\end{enumerate}
since we need to make environments like this for question parts frequently, you can make such a list more easily using the \begin{qparts}...\end{qparts} command

to make a bulleted list, it’s similar to enumerate, but the environment is called itemize instead.
to write step-by-step equations, use the align* environment. Using the align* environment, you can make columns so that your steps line up nicely. To line up columns, use the & character, and put a \\ at the end of each line. For example, here is a silly example of modular exponentiation:
\begin{align*}
3^5 & \equiv 3 \cdot (3^2)^2 \pmod{2} \\
    &\equiv 3 \cdot (9)^2 \pmod{2} \\
     &\equiv 3 \cdot 1^2 \pmod{2} \\
     & \equiv 3 \pmod{2} \\
     & \equiv 1 \pmod{2} \\
\end{align*}
it doesn’t matter if your code itself is aligned, because the environment will do it for you. an align* environment is in math mode by default, and you can use the \text{...} command to write text if you need to

to make a table, use the tabular environment. columns and rows are made in the same way as an align environment. the make horizontal lines, use the \hline command. to make a vertical line, specify it using | in curly braces after the \begin{tabular} command. For example, here is the truth table for or:
\begin{tabular}{cc|c}
$p$ & $q$ & $p \lor q$ \\
\hline
T & T & T \\
T & F & T \\
F & T & T \\
F & F & F \\
\end{tabular}
here, the cc|c means you have three center aligned columns, with the second and third separated by a vertical line. Notice that we wrapped the logic in dollar signs, since a tabular environment is in text mode by default.

to write a natural deduction proof, we use the logicproof package. logicproof also uses similar syntax to align and tabular. we start by making a \begin{logicproof}{x}...\end{logicproof} environment. here, x should be replaced by the deepest number of nested assumption boxes in your proof. each line is formatted as p & justification \\, where p is the proposition and justification is your citation. the proposition on the left of the & is in math mode by default and the justification on the right is in text mode. to make an assumption box, you put a begin{subproof} ... \end{subproof} environment inside the logicproof environment. these can be nested – that is, you can put the subproof environment inside another subproof. here is an example of a natural deduction proof:
\begin{logicproof}{1}
    p \implies q & Premise \\
    q \implies r & Premise \\
    \begin{subproof}
         p  & Assumption \\
         q  & $\implies$-elim(1, 3) \\
         r  & $\implies$-elim(2, 4) 
     \end{subproof}
      p \implies r & $\implies$-intro(3-5)
\end{logicproof}
notice how we make the argument 1 because there is one nested assumption box. also notice that we don’t put the \\ at the end of a subproof/logicproof environment. if we did, it would make an extra blank line.

#_pin



Click here to view. Search or link to this question with @12.