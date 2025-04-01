# utl-did-shakespeare-write-hamlet-nlp-of-shakespeare-plays-AI-natural-language-processing
Did shakespeare write hamlet nlp of shakespeare plays AI natural language processing
    %let pgm=utl-did-shakespeare-write-hamlet-nlp-of-shakespeare-plays-AI-natural-language-processing;

    %stop_submission;

    Did shakespeare write hamlet nlp of shakespeare plays AI natural language processing

    Once you have grammatical breakdowns of text and in addition phrase analysis, see related repos,
    you can apply a wide range of statistical analysis, principle components, logistic regression,
    neural nets, trees, forest, categorical anaysis, frequency analysis, ....


    SOAPBOX ON
      R packages are often written in C and are very fast?
    SOPABOX OFF

    github
    https://tinyurl.com/4597fb73
    https://github.com/rogerjdeangelis/utl-did-shakespeare-write-hamlet-nlp-of-shakespeare-plays-AI-natural-language-processing

    related repos
    https://github.com/rogerjdeangelis/utl_natural_language_processing_nlp_in_r_identify_nouns_pronouns_adjectives
    https://github.com/rogerjdeangelis/utl-count-of-three-word-phrases-in-a-paragraph-ngrams-nlp
    https://github.com/rogerjdeangelis/utl-finding-the-syllables-of-words-AI-NLP
    https://github.com/rogerjdeangelis/utl_how_to_find_the_union_and_intersection_of_words_in_two_strings_nlp



    communities.sas
    https://tinyurl.com/5y55rf2s
    https://communities.sas.com/t5/SAS-Programming/How-to-get-nouns-from-a-given-string/m-p/841851#M332875

    /*               _     _
     _ __  _ __ ___ | |__ | | ___ _ __ ___
    | `_ \| `__/ _ \| `_ \| |/ _ \ `_ ` _ \
    | |_) | | | (_) | |_) | |  __/ | | | | |
    | .__/|_|  \___/|_.__/|_|\___|_| |_| |_|
    |_|
    */

    /*****************************************************************************************************************************************************************/
    /*          INPUT                                          |                                          |                                                          */
    /*          =====                                          |           PROCESS                        |        OUTPUT                                            */
    /*                                                         |           =======                        |                                                          */
    /*                                                         |                                          |                                                          */
    /*  %let passage=%str(                                     |                                          | WORD        GRAMMER                                      */
    /*  To be, or not to be that is the question               | %utl_rbeginx;                            |                                                          */
    /*  Whether tis nobler in the mind to suffer               | parmcards4;                              | To          Preposition                                  */
    /*  The slings and arrows of outrageous fortune,           | library(stringr)                         | be          Verb, base form                              */
    /*  Or to take arms against a sea of troubles,             | library(NLP)                             | or          Coordinating conjunction                     */
    /*  And by opposing end them? To die to sleep              | library(openNLP)                         | not         Adverb                                       */
    /*  No more and by a sleep to say we end:);                | library(haven)                           | to          Preposition                                  */
    /*                                                         | source("c:/oto/fn_tosas9x.R")            | be          Verb, base form                              */
    /*  options validvarname=upcase;                           | txt<-read_sas("d:/sd1/have.sas7bdat")    | that        Determiner                                   */
    /*  libname sd1 "d:/sd1";                                  | txt                                      | is          Verb, 3rd person singular present            */
    /*  data sd1.have;                                         | s <- as.String(txt$TXT)                  | the         Determiner                                   */
    /*     length txt $300;                                    | sent_token_annotator<-                   | question    Noun, singular or mass                       */
    /*     txt="&passage";                                     |   Maxent_Sent_Token_Annotator()          | Whether     Preposition or subordinating conjunction     */
    /*  run;quit;                                              | word_token_annotator <-                  | tis         Noun, singular or mass                       */
    /*                                                         |   Maxent_Word_Token_Annotator()          | nobler      Noun, singular or mass                       */
    /*  proc format;                                           | a2 <- annotate(s                         | in          Preposition or subordinating conjunction     */
    /*   value $tok2grammer                                    |  ,list(sent_token_annotator              | the         Determiner                                   */
    /*    "CC  "="Coordinating conjunction                "    |  ,word_token_annotator))                 | mind        Noun, singular or mass                       */
    /*    "CD  "="Cardinal number                         "    | pos_tag_annotator <-                     | to          Preposition                                  */
    /*    "DT  "="Determiner                              "    |   Maxent_POS_Tag_Annotator()             | suffer      Verb, base form                              */
    /*    "EX  "="Existential there                       "    | pos_tag_annotator                        | The         Determiner                                   */
    /*    "FW  "="Foreign word                            "    | a3 <- annotate(s                         | slings      Noun, plural                                 */
    /*    "IN  "="Preposition or subordinating conjunction"    |   ,pos_tag_annotator                     | and         Coordinating conjunction                     */
    /*    "JJ  "="Adjective                               "    |   ,a2)                                   | arrows      Noun, plural                                 */
    /*    "JJR "="Adjective, comparative                  "    | a3;                                      | of          Preposition or subordinating conjunction     */
    /*    "JJS "="Adjective, superlative                  "    | head(annotate(s                          | outrageous  Adjective                                    */
    /*    "LS  "="List item marker                        "    |  ,Maxent_POS_Tag_Annotator(probs=TRUE)   | fortune     Noun, singular or mass                       */
    /*    "MD  "="Modal                                   "    |  ,a2))                                   | Or          Coordinating conjunction                     */
    /*    "NN  "="Noun, singular or mass                  "    | a3w <- subset(a3, type == "word")        | to          Preposition                                  */
    /*    "NNS "="Noun, plural                            "    | tags <- sapply(a3w$features,`[[`,"POS")  | take        Verb, base form                              */
    /*    "NNP "="Proper noun, singular                   "    | tags                                     | arms        Noun, plural                                 */
    /*    "NNPS"="Proper noun, plural                     "    | table(tags)                              | against     Preposition or subordinating conjunction     */
    /*    "PDT "="Predeterminer                           "    | want<-as.data.frame(sprintf("%s/%s"      | sea         Noun, singular or mass                       */
    /*    "POS "="Possessive ending                       "    |  ,s[a3w], tags))                         | of          Preposition or subordinating conjunction     */
    /*    "PRP "="Personal pronoun                        "    | colnames(want)<-"wrdGrm"                 | troubles    Noun, plural                                 */
    /*    "PRP$"="Possessive pronoun                      "    | want                                     | And         Coordinating conjunction                     */
    /*    "RB  "="Adverb                                  "    | fn_tosas9x(                              | by          Preposition or subordinating conjunction     */
    /*    "RBR "="Adverb, comparative                     "    |       inp    = want                      | opposing    Verb, gerund or present participle           */
    /*    "RBS "="Adverb, superlative                     "    |      ,outlib ="d:/sd1/"                  | end         Noun, singular or mass                       */
    /*    "RP  "="Particle                                "    |      ,outdsn ="want"                     | them        Personal pronoun                             */
    /*    "SYM "="Symbol                                  "    |      )                                   | To          Preposition                                  */
    /*    "UH  "="Interjection                            "    | ;;;;                                     | die         Verb, base form                              */
    /*    "VB  "="Verb, base form                         "    | %utl_rendx;                              | to          Preposition                                  */
    /*    "VBD "="Verb, past tense                        "    |                                          | sleep       Verb, base form                              */
    /*    "VBG "="Verb, gerund or present participle      "    | data WANT;                               | No          Determiner                                   */
    /*    "VBN "="Verb, past participle                   "    |   set sd1.want;                          | more        Adverb, comparative                          */
    /*    "VBP "="Verb, non­3rd person singular present   "    |   word=scan(wrdGrm,1,'/');               | and         Coordinating conjunction                     */
    /*    "VBZ "="Verb, 3rd person singular present       "    |   grm=scan(wrdGrm,2,'/');                | by          Preposition or subordinating conjunction     */
    /*    "WDT "="Wh­determiner                           "    | if length(word)>1;                       | sleep       Noun, singular or mass                       */
    /*    "WP  "="Wh­pronoun                              "    |   grammer=put(strip(grm)                 | to          Preposition                                  */
    /*    "WP$ "="Possessive wh­pronoun                   "    |   ,$tok2grammer.);                       | say         Verb, base form                              */
    /*    "WRB "="Wh­adverb                               "    |   keep word grammer;                     | we          Personal pronoun                             */
    /*    other="Preposition"                                  | run;quit;                                | end         Noun, singular or mass                       */
    /*  ;run;quit;                                             |                                          |                                                          */
    /******************************************************************************************************************************************************************/


    /*                   _
    (_)_ __  _ __  _   _| |_
    | | `_ \| `_ \| | | | __|
    | | | | | |_) | |_| | |_
    |_|_| |_| .__/ \__,_|\__|
            |_|
    */

    %let passage=%str(
    To be  or not to be that is the question
    Whether tis nobler in the mind to suffer
    The slings and arrows of outrageous fortune
    Or to take arms against a sea of troubles
    And by opposing end them To die to sleep
    No more and by a sleep to say we end);

    options validvarname=upcase;
    libname sd1 "d:/sd1";
    data sd1.have;
       length txt $300;
       txt="&passage";
    run;quit;

    proc format;
     value $tok2grammer
      "CC  "="Coordinating conjunction                "
      "CD  "="Cardinal number                         "
      "DT  "="Determiner                              "
      "EX  "="Existential there                       "
      "FW  "="Foreign word                            "
      "IN  "="Preposition or subordinating conjunction"
      "JJ  "="Adjective                               "
      "JJR "="Adjective, comparative                  "
      "JJS "="Adjective, superlative                  "
      "LS  "="List item marker                        "
      "MD  "="Modal                                   "
      "NN  "="Noun, singular or mass                  "
      "NNS "="Noun, plural                            "
      "NNP "="Proper noun, singular                   "
      "NNPS"="Proper noun, plural                     "
      "PDT "="Predeterminer                           "
      "POS "="Possessive ending                       "
      "PRP "="Personal pronoun                        "
      "PRP$"="Possessive pronoun                      "
      "RB  "="Adverb                                  "
      "RBR "="Adverb, comparative                     "
      "RBS "="Adverb, superlative                     "
      "RP  "="Particle                                "
      "SYM "="Symbol                                  "
      "UH  "="Interjection                            "
      "VB  "="Verb, base form                         "
      "VBD "="Verb, past tense                        "
      "VBG "="Verb, gerund or present participle      "
      "VBN "="Verb, past participle                   "
      "VBP "="Verb, non­3rd person singular present   "
      "VBZ "="Verb, 3rd person singular present       "
      "WDT "="Wh­determiner                           "
      "WP  "="Wh­pronoun                              "
      "WP$ "="Possessive wh­pronoun                   "
      "WRB "="Wh­adverb                               "
      other="Preposition"
    ;run;quit;

    /*
     _ __  _ __ ___   ___ ___  ___ ___
    | `_ \| `__/ _ \ / __/ _ \/ __/ __|
    | |_) | | | (_) | (_|  __/\__ \__ \
    | .__/|_|  \___/ \___\___||___/___/
    |_|
    */

    %utl_rbeginx;
    parmcards4;
    library(stringr)
    library(NLP)
    library(openNLP)
    library(haven)
    source("c:/oto/fn_tosas9x.R")
    txt<-read_sas("d:/sd1/have.sas7bdat")
    txt
    s <- as.String(txt$TXT)
    sent_token_annotator<-
      Maxent_Sent_Token_Annotator()
    word_token_annotator <-
      Maxent_Word_Token_Annotator()
    a2 <- annotate(s
     ,list(sent_token_annotator
     ,word_token_annotator))
    pos_tag_annotator <-
      Maxent_POS_Tag_Annotator()
    pos_tag_annotator
    a3 <- annotate(s
      ,pos_tag_annotator
      ,a2)
    a3;
    head(annotate(s
     ,Maxent_POS_Tag_Annotator(probs=TRUE)
     ,a2))
    a3w <- subset(a3, type == "word")
    tags <- sapply(a3w$features,`[[`,"POS")
    tags
    table(tags)
    want<-as.data.frame(sprintf("%s/%s"
     ,s[a3w], tags))
    colnames(want)<-"wrdGrm"
    want
    fn_tosas9x(
          inp    = want
         ,outlib ="d:/sd1/"
         ,outdsn ="want"
         )
    ;;;;
    %utl_rendx;

    data want;
      set sd1.want;
      word=scan(wrdGrm,1,'/');
      grm=scan(wrdGrm,2,'/');
      grammer=put(strip(grm)
      ,$tok2grammer.);
      keep word grammer;
    run;quit;

    /**************************************************************************************************************************/
    /* R                    | SAS (AFTER USING THE FORMAT LOOKUP)                                                             */
    /*                      |                                                                                                 */
    /*           wrdGrm     | WORD          GRAMMER                                                                           */
    /*                      |                                                                                                 */
    /* 1          To/TO     | To            Preposition                                                                       */
    /* 2          be/VB     | be            Verb, base form                                                                   */
    /* 3          or/CC     | or            Coordinating conjunction                                                          */
    /* 4         not/RB     | not           Adverb                                                                            */
    /* 5          to/TO     | to            Preposition                                                                       */
    /* 6          be/VB     | be            Verb, base form                                                                   */
    /* 7        that/DT     | that          Determiner                                                                        */
    /* 8         is/VBZ     | is            Verb, 3rd person singular present                                                 */
    /* 9         the/DT     | the           Determiner                                                                        */
    /* 10   question/NN     | question      Noun, singular or mass                                                            */
    /* 11    Whether/IN     | Whether       Preposition or subordinating conjunction                                          */
    /* 12        tis/NN     | tis           Noun, singular or mass                                                            */
    /* 13     nobler/NN     | nobler        Noun, singular or mass                                                            */
    /* 14         in/IN     | in            Preposition or subordinating conjunction                                          */
    /* 15        the/DT     | the           Determiner                                                                        */
    /* 16       mind/NN     | mind          Noun, singular or mass                                                            */
    /* 17         to/TO     | to            Preposition                                                                       */
    /* 18     suffer/VB     | suffer        Verb, base form                                                                   */
    /* 19        The/DT     | The           Determiner                                                                        */
    /* 20    slings/NNS     | slings        Noun, plural                                                                      */
    /* 21        and/CC     | and           Coordinating conjunction                                                          */
    /* 22    arrows/NNS     | arrows        Noun, plural                                                                      */
    /* 23         of/IN     | of            Preposition or subordinating conjunction                                          */
    /* 24 outrageous/JJ     | outrageous    Adjective                                                                         */
    /* 25    fortune/NN     | fortune       Noun, singular or mass                                                            */
    /* 26         Or/CC     | Or            Coordinating conjunction                                                          */
    /* 27         to/TO     | to            Preposition                                                                       */
    /* 28       take/VB     | take          Verb, base form                                                                   */
    /* 29      arms/NNS     | arms          Noun, plural                                                                      */
    /* 30    against/IN     | against       Preposition or subordinating conjunction                                          */
    /* 31          a/DT     | a             Determiner                                                                        */
    /* 32        sea/NN     | sea           Noun, singular or mass                                                            */
    /* 33         of/IN     | of            Preposition or subordinating conjunction                                          */
    /* 34  troubles/NNS     | troubles      Noun, plural                                                                      */
    /* 35        And/CC     | And           Coordinating conjunction                                                          */
    /* 36         by/IN     | by            Preposition or subordinating conjunction                                          */
    /* 37  opposing/VBG     | opposing      Verb, gerund or present participle                                                */
    /* 38        end/NN     | end           Noun, singular or mass                                                            */
    /* 39      them/PRP     | them          Personal pronoun                                                                  */
    /* 40         To/TO     | To            Preposition                                                                       */
    /* 41        die/VB     | die           Verb, base form                                                                   */
    /* 42         to/TO     | to            Preposition                                                                       */
    /* 43      sleep/VB     | sleep         Verb, base form                                                                   */
    /* 44         No/DT     | No            Determiner                                                                        */
    /* 45      more/RBR     | more          Adverb, comparative                                                               */
    /* 46        and/CC     | and           Coordinating conjunction                                                          */
    /* 47         by/IN     | by            Preposition or subordinating conjunction                                          */
    /* 48          a/DT     | a             Determiner                                                                        */
    /* 49      sleep/NN     | sleep         Noun, singular or mass                                                            */
    /* 50         to/TO     | to            Preposition                                                                       */
    /* 51        say/VB     | say           Verb, base form                                                                   */
    /* 52        we/PRP     | we            Personal pronoun                                                                  */
    /* 53        end/NN     | end           Noun, singular or mass                                                            */
    /************************|*************************************************************************************************/

    /*              _
      ___ _ __   __| |
     / _ \ `_ \ / _` |
    |  __/ | | | (_| |
     \___|_| |_|\__,_|

    */



























































|
|
|
|
|
|
|


        To      To
        be      be
        or      or
       not      not
        to      to
        be      be
      that      that
       is       is
       the      the
  question      question
   Whether      Whether
       tis      tis
    nobler      nobler
        in      in
       the      the
      mind      mind
        to      to
    suffer      suffer
       The      The
   slings       slings
       and      and
   arrows       arrows
        of      of
outrageous      outrageous
   fortune      fortune
        Or      Or
        to      to
      take      take
     arms       arms
   against      against
         a      sea
       sea      of
        of      troubles
 troubles       And
       And      by
        by      opposing
 opposing       end
       end      them
     them       To
          .     die
        To      to
       die      sleep
        to      No
     sleep      more
        No      and
     more       by
       and      sleep
        by      to
         a      say
     sleep      we
        to      end
       say
       we
       end











           INPUT
           =====                                                     PROCESS                                OUTPUT
                                                                     =======

   %let passage=%str(                                                                                WORD          GRAMMER
   To be, or not to be that is the question                %utl_rbeginx;
   Whether tis nobler in the mind to suffer                parmcards4;                               To            Preposition
   The slings and arrows of outrageous fortune,            library(stringr)                          be            Verb, base form
   Or to take arms against a sea of troubles,              library(NLP)                              or            Coordinating conjunction
   And by opposing end them? To die to sleep               library(openNLP)                          not           Adverb
   No more and by a sleep to say we end:);                 library(haven)                            to            Preposition
                                                           source("c:/oto/fn_tosas9x.R")             be            Verb, base form
   options validvarname=upcase;                            txt<-read_sas("d:/sd1/have.sas7bdat")     that          Determiner
   libname sd1 "d:/sd1";                                   txt                                       is            Verb, 3rd person singular present
   data sd1.have;                                          s <- as.String(txt$TXT)                   the           Determiner
      length txt $300;                                     sent_token_annotator<-                    question      Noun, singular or mass
      txt="&passage";                                        Maxent_Sent_Token_Annotator()           Whether       Preposition or subordinating conjunction
   run;quit;                                               word_token_annotator <-                   tis           Noun, singular or mass
                                                             Maxent_Word_Token_Annotator()           nobler        Noun, singular or mass
   proc format;                                            a2 <- annotate(s                          in            Preposition or subordinating conjunction
    value $tok2grammer                                      ,list(sent_token_annotator               the           Determiner
     "CC  "="Coordinating conjunction                "      ,word_token_annotator))                  mind          Noun, singular or mass
     "CD  "="Cardinal number                         "     pos_tag_annotator <-                      to            Preposition
     "DT  "="Determiner                              "       Maxent_POS_Tag_Annotator()              suffer        Verb, base form
     "EX  "="Existential there                       "     pos_tag_annotator                         The           Determiner
     "FW  "="Foreign word                            "     a3 <- annotate(s                          slings        Noun, plural
     "IN  "="Preposition or subordinating conjunction"       ,pos_tag_annotator                      and           Coordinating conjunction
     "JJ  "="Adjective                               "       ,a2)                                    arrows        Noun, plural
     "JJR "="Adjective, comparative                  "     a3;                                       of            Preposition or subordinating conjunction
     "JJS "="Adjective, superlative                  "     head(annotate(s                           outrageous    Adjective
     "LS  "="List item marker                        "      ,Maxent_POS_Tag_Annotator(probs=TRUE)    fortune       Noun, singular or mass
     "MD  "="Modal                                   "      ,a2))                                    Or            Coordinating conjunction
     "NN  "="Noun, singular or mass                  "     a3w <- subset(a3, type == "word")         to            Preposition
     "NNS "="Noun, plural                            "     tags <- sapply(a3w$features,`[[`,"POS")   take          Verb, base form
     "NNP "="Proper noun, singular                   "     tags                                      arms          Noun, plural
     "NNPS"="Proper noun, plural                     "     table(tags)                               against       Preposition or subordinating conjunction
     "PDT "="Predeterminer                           "     want<-as.data.frame(sprintf("%s/%s"       sea           Noun, singular or mass
     "POS "="Possessive ending                       "      ,s[a3w], tags))                          of            Preposition or subordinating conjunction
     "PRP "="Personal pronoun                        "     colnames(want)<-"wrdGrm"                  troubles      Noun, plural
     "PRP$"="Possessive pronoun                      "     want                                      And           Coordinating conjunction
     "RB  "="Adverb                                  "     fn_tosas9x(                               by            Preposition or subordinating conjunction
     "RBR "="Adverb, comparative                     "           inp    = want                       opposing      Verb, gerund or present participle
     "RBS "="Adverb, superlative                     "          ,outlib ="d:/sd1/"                   end           Noun, singular or mass
     "RP  "="Particle                                "          ,outdsn ="want"                      them          Personal pronoun
     "SYM "="Symbol                                  "          )                                    To            Preposition
     "UH  "="Interjection                            "     ;;;;                                      die           Verb, base form
     "VB  "="Verb, base form                         "     %utl_rendx;                               to            Preposition
     "VBD "="Verb, past tense                        "                                               sleep         Verb, base form
     "VBG "="Verb, gerund or present participle      "                                               No            Determiner
     "VBN "="Verb, past participle                   "                                               more          Adverb, comparative
     "VBP "="Verb, non­3rd person singular present   "                                               and           Coordinating conjunction
     "VBZ "="Verb, 3rd person singular present       "                                               by            Preposition or subordinating conjunction
     "WDT "="Wh­determiner                           "                                               sleep         Noun, singular or mass
     "WP  "="Wh­pronoun                              "                                               to            Preposition
     "WP$ "="Possessive wh­pronoun                   "                                               say           Verb, base form
     "WRB "="Wh­adverb                               "                                               we            Personal pronoun
     other="Preposition"                                                                             end           Noun, singular or mass
   ;run;quit;




%utl_rbeginx;
parmcards4;
library(stringr)
library(NLP)
library(openNLP)
library(haven)
Sys.setenv(JAVA_HOME = "C:\\Program Files\\Microsoft\\jdk-11.0.26.4-hotspot");
source("c:/oto/fn_tosas9x.R")
txt<-read_sas("d:/sd1/have.sas7bdat")
s <- as.String(txt$TXT)
sent_token_annotator
  <- Maxent_Sent_Token_Annotator()
;;;;
%utl_rendx;

word_token_annotator <-
  Maxent_Word_Token_Annotator()
a2 <- annotate(s
 ,list(sent_token_annotator
 ,word_token_annotator))
pos_tag_annotator <-
  Maxent_POS_Tag_Annotator()
pos_tag_annotator
a3 <- annotate(s
   ,pos_tag_annotator
   ,a2)
head(annotate(s
 ,Maxent_POS_Tag_Annotator(probs=TRUE)
 ,a2));
a3w <- subset(a3, type == "word")
tags <- sapply(a3w$features, `[[`, "POS")
tags;
table(tags)
want<-as.data.frame(
  sprintf("%s/%s"
 ,s[a3w], tags))
colnames(want)<-"wrdGrm"
want;
fn_tosas9x(
      inp    = want
     ,outlib ="d:/sd1/"
     ,outdsn ="want"
     )
;;;;
%utl_rendx;


       s <- as.String(txt$TXT);
       sent_token_annotator <- Maxent_Sent_Token_Annotator();
       word_token_annotator <- Maxent_Word_Token_Annotator();
       a2 <- annotate(s, list(sent_token_annotator, word_token_annotator));
       pos_tag_annotator <- Maxent_POS_Tag_Annotator();
       pos_tag_annotator;
       a3 <- annotate(s, pos_tag_annotator, a2);


https://github.com/rogerjdeangelis/utl-count-of-three-word-phrases-in-a-paragraph-ngrams-nlp
https://github.com/rogerjdeangelis/utl-finding-the-syllables-of-words-AI-NLP
https://github.com/rogerjdeangelis/utl_how_to_find_the_union_and_intersection_of_words_in_two_strings_nlp
https://github.com/rogerjdeangelis/utl_natural_language_processing_nlp_in_r_identify_nouns_pronouns_adjectives



/*                   _
(_)_ __  _ __  _   _| |_
| | `_ \| `_ \| | | | __|
| | | | | |_) | |_| | |_
|_|_| |_| .__/ \__,_|\__|
        |_|
*/





%let passage=%str(
To be, or not to be that is the question
Whether tis nobler in the mind to suffer
The slings and arrows of outrageous fortune,
Or to take arms against a sea of troubles,
And by opposing end them? To die to sleep
No more and by a sleep to say we end:);

%put &=passage;

options validvarname=upcase;
libname sd1 "d:/sd1";
data sd1.have;
   length txt $300;
   txt="&passage";
run;quit;







%utl_rbeginx;
parmcards4;
library(stringr)
library(NLP)
library(openNLP)
library(haven)
source("c:/oto/fn_tosas9x.R")
txt<-read_sas("d:/sd1/have.sas7bdat")
txt
s <- as.String(txt$TXT)
sent_token_annotator<-
  Maxent_Sent_Token_Annotator()
word_token_annotator <-
  Maxent_Word_Token_Annotator()
a2 <- annotate(s
 ,list(sent_token_annotator
 ,word_token_annotator))
pos_tag_annotator <-
  Maxent_POS_Tag_Annotator()
pos_tag_annotator
a3 <- annotate(s
  ,pos_tag_annotator
  ,a2)
a3;
head(annotate(s
 ,Maxent_POS_Tag_Annotator(probs=TRUE)
 ,a2))
a3w <- subset(a3, type == "word")
tags <- sapply(a3w$features,`[[`,"POS")
tags
table(tags)
want<-as.data.frame(sprintf("%s/%s"
 ,s[a3w], tags))
colnames(want)<-"wrdGrm"
want
fn_tosas9x(
      inp    = want
     ,outlib ="d:/sd1/"
     ,outdsn ="want"
     )
;;;;
%utl_rendx;






%utl_rbeginx;
parmcards4;
library(stringr);
library(NLP);
library(openNLP);
library(haven);
Sys.setenv(JAVA_HOME = "C:\\Program Files\\Microsoft\\jdk-11.0.26.4-hotspot");
source("c:/oto/fn_tosas9x.R")
txt<-read_sas("d:/sd1/have.sas7bdat");
txt;
s <- as.String(txt$TXT);
sent_token_annotator <- Maxent_Sent_Token_Annotator();
word_token_annotator <- Maxent_Word_Token_Annotator();
a2 <- annotate(s, list(sent_token_annotator, word_token_annotator));
pos_tag_annotator <- Maxent_POS_Tag_Annotator();
pos_tag_annotator;
a3 <- annotate(s, pos_tag_annotator, a2);
a3;
head(annotate(s, Maxent_POS_Tag_Annotator(probs = TRUE), a2));
a3w <- subset(a3, type == "word");
tags <- sapply(a3w$features, `[[`, "POS");
tags;
table(tags);
want<-as.data.frame(sprintf("%s/%s", s[a3w], tags));
colnames(want)<-"wrdGrm";
want;
fn_tosas9x(
      inp    = want
     ,outlib ="d:/sd1/"
     ,outdsn ="want"
     )
;;;;
%utl_rendx;


proc print data=sd1.want;
run;quit;

data WANT;
  set sd1.want;
  word=scan(wrdGrm,1,'/');
  grm=scan(wrdGrm,2,'/');
if length(word)>1;
  grammer=put(strip(grm)
  ,$tok2grammer.);
  keep word grammer;
run;quit;



  1        1       To/TO
  2        2       be/VB
  3        3       ,/,
  4        4       or/CC
  5        5       not/RB
  6        6       to/TO
  7        7       be/VB
  8        8       :/:
  9        9       that/DT
 10       10       is/VBZ
 11       11       the/DT
 12       12       question/NN
 13       13       :/:
 14       14       Whether/IN
 15       15       tis/NN
 16       16       nobler/NN
 17       17       in/IN
 18       18       the/DT
 19       19       mind/NN
 20       20       to/TO
 21       21       suffer/VB
 22       22       The/DT
 23       23       slings/NNS
 24       24       and/CC
 25       25       arrows/NNS
 26       26       of/IN
 27       27       outrageous/JJ
 28       28       fortune/NN
 29       29       ,/,
 30       30       Or/CC
 31       31       to/TO
 32       32       take/VB
 33       33       arms/NNS
 34       34       against/IN
 35       35       a/DT
 36       36       sea/NN
 37       37       of/IN
 38       38       troubles/NNS
 39       39       ,/,
 40       40       And/CC
 41       41       by/IN
 42       42       opposing/VBG
 43       43       end/NN
 44       44       them/PRP
 45       45       ?/.
 46       46       To/TO
 47       47       die/VB
 48       48       :/:
 49       49       to/TO
 50       50       sleep/VB
 51       51       :/:
 52       52       No/DT
 53       53       more/RBR
 54       54       :/:
 55       55       and/CC
 56       56       by/IN
 57       57       a/DT
 58       58       sleep/NN
 59       59       to/TO
 60       60       say/VB
 61       61       we/PRP















































proc format;
  value $tok2grammer
     "CC  "="Coordinating conjunction                "
     "CD  "="Cardinal number                         "
     "DT  "="Determiner                              "
     "EX  "="Existential there                       "
     "FW  "="Foreign word                            "
     "IN  "="Preposition or subordinating conjunction"
     "JJ  "="Adjective                               "
     "JJR "="Adjective, comparative                  "
     "JJS "="Adjective, superlative                  "
     "LS  "="List item marker                        "
     "MD  "="Modal                                   "
     "NN  "="Noun, singular or mass                  "
     "NNS "="Noun, plural                            "
     "NNP "="Proper noun, singular                   "
     "NNPS"="Proper noun, plural                     "
     "PDT "="Predeterminer                           "
     "POS "="Possessive ending                       "
     "PRP "="Personal pronoun                        "
     "PRP$"="Possessive pronoun                      "
     "RB  "="Adverb                                  "
     "RBR "="Adverb, comparative                     "
     "RBS "="Adverb, superlative                     "
     "RP  "="Particle                                "
     "SYM "="Symbol                                  "
     "UH  "="Interjection                            "
     "VB  "="Verb, base form                         "
     "VBD "="Verb, past tense                        "
     "VBG "="Verb, gerund or present participle      "
     "VBN "="Verb, past participle                   "
     "VBP "="Verb, non­3rd person singular present   "
     "VBZ "="Verb, 3rd person singular present       "
     "WDT "="Wh­determiner                           "
     "WP  "="Wh­pronoun                              "
     "WP$ "="Possessive wh­pronoun                   "
     "WRB "="Wh­adverb                               "
     other="Preposition"
 ;run;quit;


%let passage=%str(
To be, or not to be: that is the question:
Whether tis nobler in the mind to suffer
The slings and arrows of outrageous fortune,
Or to take arms against a sea of troubles,
And by opposing end them? To die: to sleep;
No more; and by a sleep to say we end;);

%put &passage;
