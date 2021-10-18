<section class="main_content">
    <div class="post" itemscope="" itemtype="http://schema.org/BlogPosting">
      <div class="alert" id="alert" style="display: block;">Check out my online course: <a href="http://www.bradoncode.com/blog/2015/11/19/angularjs-unit-testing-course-pluralsight/">AngularJS Unit Testing in-depth with ngMock</a>.</div>

      <h1 itemprop="headline">Developer Testing - Why should developers write tests?</h1>
      <p class="summary">What are the different types of tests for software, and why should developers write them?</p>
      <div class="post_detail">
        <span class="icon">
          <span itemprop="author" itemscope="" itemtype="http://schema.org/Person">
            <span itemprop="name">
              <a href="http://www.bradoncode.com/about" itemprop="url" rel="author">Bradley Braithwaite</a>
            </span>
          </span> on 
          <time itemprop="datePublished" datetime="2015-05-10T00:00:00+00:00">May 10, 2015</time>
          <br class="tagwrap">
            
            
            on 
            <span class="tags">musings, testing</span>
            
        </span>
      </div>
      <div class="post" itemprop="articleBody">
        <p>The <a href="https://docs.angularjs.org/guide/unit-testing">section about testing</a> from the AngularJS documentation has the following sentence which caught my attention (with emphasis mine):</p>

<blockquote>
  <p>Angular is written with testability in mind, <strong>but it still requires that you do the right thing</strong>. We tried to make the right things easy, but if you ignore these guidelines you may end up with an untestable application.</p>
</blockquote>

<p>But, what’s the right thing? Those few words are packed full of subtle nuances and trade-offs that can lead to <a href="http://martinfowler.com/articles/is-tdd-dead/">high-profile nerd wars</a> and heated twitter exchanges. I plan to write a lot more about testing with AngularJS on this blog (<a href="http://feeds.bradoncode.com/bradoncode">subscribe to the RSS feed</a> if you would like to keep up-to-date), but before I start writing technical posts I want to address why I think tests are important. I personally think that you have nothing to lose in getting started… perhaps just the bugs in your code!</p>

<p><img src="https://lh3.googleusercontent.com/gxSd7zrkK8npfcR8bF_he0eXN7EjUY9LyslWyaXpILg=w587-h364-no" alt="developer tests"></p>
<div class="caption">The effect of test coverage?</div>

<h2 id="different-types-of-tests">Different Types of Tests</h2>

<p>The common types of tests that developers can write for applications are:</p>

<ol>
  <li>Unit Tests</li>
  <li>Integration Tests</li>
  <li>Regression Tests</li>
  <li>System Tests</li>
</ol>

<h3 id="1-unit-tests">1. Unit Tests</h3>

<p>Unit Testing is the execution of a section of code or small program which is tested in isolation from the more complete system. Tested in isolation means not calling the implementation of code not under test e.g. database, web service calls or other code dependencies. The concept of isolation is why mocking frameworks are commonly used for unit tests. These would be written by developers during the development of a feature.</p>

<h3 id="2-integration-tests">2. Integration Tests</h3>

<p>Integration Testing is the combined execution sections of code. In these types of tests you would hit the database, make web service calls or call other code dependencies. These would be written by developers. These would be written by developers during the development of a feature.</p>

<h3 id="3-regression-tests">3. Regression Tests</h3>

<p>Regression testing is the repetition of previously executed test cases for the purpose of finding defects in software that previously passed the same set of tests. Such tests would commonly be used before shipping code to a new environment or as part of a build process. It’s common to see tools such a selenium used to write these types of tests, where a web browser would be launched and user input automated. Human testers can also perform regression tests by using an application directly.</p>

<h3 id="4-system-tests">4. System Tests</h3>

<p>System testing is the execution of the software in its final configuration, including integration with other software and systems. It tests for security, performance, resource loss, timing problems, and other issues that can’t be tested at lower levels of integration. As with regression testing, automated tools such as selenium can be used for this process as well as human testers.</p>

<h2 id="different-approaches-to-writing-developer-tests">Different Approaches to Writing Developer Tests</h2>

<p><em>Developer tests</em> are written whilst the developer is writing the actual functionality. This process is tightly integrated so that the developer can work in a flow of writing tests and the logic. There are two widely adopted approaches for writing developer tests:</p>

<ol>
  <li>Test Driven Development (TDD)</li>
  <li>Behaviour Driven Development (BDD)</li>
</ol>

<p>These different approaches are often the main point of contention amongst developers when setting out a testing strategy. Note that developer tests do not consider Regression or System Tests. Developers can also write code to automate Regression and/or System Tests, but that would come at a later stage in the development cycle when the application is in a more complete state. Regression or System Tests are sometimes even written by a different developer who specialises in writing regression tests and views the system as a black-box i.e. is not aware of the internal workings.</p>

<h3 id="1-test-driven-development---tdd">1. Test Driven Development - TDD</h3>

<p>Using <strong>TDD you write Unit Tests</strong> that are driven by the implementation detail of the code. With unit tests, we must test things in isolation. If following the style as intended, the developer must code in a <em>“Red, Green, Refactor”</em> style, where they first write a test, watch the test fail (since the logic is not yet implemented), then write enough code to make the test pass, before refactoring the code and ensuring that the test still passes. Once a developer has finished working through a feature they will be left with a suite of passing tests verifying the correctness of their implementation.</p>

<h3 id="2-behaviour-driven-development---bdd">2. Behaviour Driven Development - BDD</h3>

<p>Using <strong>BDD you write Integration Tests</strong> that are driven by application behaviour which is in contrast to TDD which concerns itself with the implementation detail. You are also not restricted to testing in isolation as with TDD. In fact, BDD has emerged from TDD which has been around for longer. As with TDD, you would write tests before implementing the logic and make each test pass when moving through the implementation. Once a feature is completed the developer is left with a suite of passing tests verifying the correctness of the behaviour of the code.</p>

<h2 id="why-i-like-to-write-developer-tests">Why I like to write Developer Tests</h2>

<p>What I like to get from developer tests, regardless of approach (TDD or BDD) is to:</p>

<ol>
  <li>Write Fewer Bugs</li>
  <li>Avoid Manual Testing</li>
  <li>Get a Faster Feedback Loop</li>
  <li>Increased Confidence when Changing Code</li>
</ol>

<h3 id="1-write-fewer-bugs">1. Write Fewer Bugs</h3>

<p>This seems like an obvious point, but I’ve had discussions with developers who do not write tests as in their view, developers should check their work anyway and that they have testers who can catch regressions, therefore the tests are unnecessary additional code. A study by Glenford Myers in 1978 had a group of experienced programmers test a program with 15 known defects. <strong>The average programmer only found 5 of the bugs</strong>. In the study the main source of the errors that went unnoticed was erroneous output not being looked at closely enough. The conclusion of this? Humans are error-prone.</p>

<p>It’s important to recognise that writing tests does not guarantee zero bugs. There is still plenty that can go wrong such as database problems, mistakes with functionality, integration problems and so on, so there will always be a need for testers.</p>

<h3 id="2-avoid-manual-testing">2. Avoid Manual Testing</h3>

<p>The process of testing code after making changes can be very time consuming, and as we’ve already established, is prone to human error. The book <a href="http://cc2e.com">Code Complete</a> indicates that <strong>developer testing takes 8 to 25 percent of the total project time</strong> dependant on project size and complexity. That’s 16.5% on average, or around an hour per 8 hour working day. This means that we developers will spend a lot of time testing the code we write, so any approach to streamline this process is worth serious consideration.</p>

<p>The following pie chart is the approximate percentage breakdown of developer time spent on a project with 2,000 lines of code:</p>

<p><img src="https://lh3.googleusercontent.com/-N4KekoJzCbU/VU6PSPoDufI/AAAAAAAABbQ/sbKVr-3Igmc/w464-h209-no/code-complete-2k.png" alt="Percentage of Development Time"></p>
<div class="caption">Percentage of Development Time for 2k lines of code</div>

<h3 id="3-get-a-faster-feedback-loop">3. Get a Faster Feedback Loop</h3>

<p>A feedback loop is the cycle of adding some code, getting feedback about the change i.e. is ok/not ok, then repeating. For me, the faster this cycle, the more productive I am. Increasing productivity and reducing the number of bugs we write sounds like an idealistic programmer utopia, but once a programmer cultivates a flow for writing tests I believe that this is possible.</p>

<h3 id="4-increased-confidence-when-changing-code">4. Increased Confidence when Changing Code</h3>

<p>Have you worked on a feature and spotted something you thought could be improved with the existing code, but chose not to correct it because you didn’t want to risk creating more work for yourself by potentially breaking something? Good test coverage provides a safety net for making such changes, making you and the other developers in your team more likely to refactor that code smell. The net effect of this is a better code-base for you all.</p>

<p>Tests by themselves do not improve software quality. The process of writing code that is testable, and the safety net of being able to refactor code and (almost) be sure that it does not result in a regression, is where the improvements occur.</p>

<h2 id="summary">Summary</h2>

<p>This post has introduced the main concepts of writing developer tests, and how the types of tests integrate with the approaches for writing tests. The high-level differences between TDD and BDD have been discussed and all that’s left now is to start looking at code examples. The code examples will come in future posts where I will be covering testing using AngularJS extensively.</p>

<p>My thoughts on writing tests are aligned with this quote from <a href="http://www.growing-object-oriented-software.com">Growing Object-Oriented Software, Guided by Tests</a>:</p>

<blockquote>
  <p>If we write tests all the way through the development process, we can build up a safety net of automated regression tests that give us the confidence to make changes.</p>
</blockquote>

<p><a href="http://feeds.bradoncode.com/bradoncode">Subscribe to the RSS feed</a> if you want to learn about developer testing with AngularJS.</p>


        
      </div>
    </div>
    <div class="sharebot">
	<div>SHARE</div>
	<!--
<div class="addthis_sharing_toolbox"></div>
 <div class="sharelinks">
	<a href="http://twitter.com/intent/tweet?url=http://www.bradoncode.com/blog/2015/05/10/developer-testing/&amp;text=Developer Testing - Why should developers write tests? via @bradoncode" title="share twitter" id="twl">Twitter</a>
	<a href="http://facebook.com/sharer.php?u=http://www.bradoncode.com/blog/2015/05/10/developer-testing/" title="share facebook" id="fb">Facebook</a>
	<a href="https://plus.google.com/share?url=http://www.bradoncode.com/blog/2015/05/10/developer-testing/" title="share google+" id="gp">Google+</a>
</div> -->

<!-- 	<p><span>Find me on Twitter:</span></p>
	<p>
    <a href="https://twitter.com/bradoncode" class="twitter-follow-button" data-show-count="false">Follow @bradoncode</a>
  </p> -->
</div>
    <div style="padding: 20px 0;background-color:#fafafa;border-radius: 10px;text-align:center;">
	<span>Don't miss out on the free technical content:</span>
	<br><br>
	<a href="http://www.bradoncode.com/subscribe" class="btn">Subscribe to Updates</a>
</div>
    <div itemscope="" itemtype="http://schema.org/Person" class="about">
   <h4>CONNECT WITH BRADLEY</h4>
   <img src="http://s.gravatar.com/avatar/df748782822137c518f3eebb0bbaadfc?s=95" alt="Bradley Braithwaite Software Blog" width="95" height="95" itemprop="image" class="img" style="float:left;">
   <span itemprop="name">Bradley Braithwaite</span> is a <span itemprop="jobTitle">software engineer</span> who works for search engine start-ups. He is a published author at <a class="vglnk" href="http://pluralsight.com" rel="nofollow"><span>pluralsight</span><span>.</span><span>com</span></a>. He writes about software development practices, JavaScript, AngularJS and Node.js via his website <a href="http://www.bradoncode.com" itemprop="url">bradoncode.com</a>. Find out more <a href="/about/">about Brad</a>. Find him via:
   <div class="sociallinks">
   	<a href="https://twitter.com/bradoncode" id="tw">Twitter</a>
   </div>
</div>

      <div class="feature">
    <div class="heading">You might also like:</div>
    <a href="http://www.bradoncode.com/tutorials/learn-mean-stack-tutorial/" title="mean stack tutorial"><img src="http://www.bradoncode.com/assets/img/mean-stack-tutorial.png" alt="mean stack tutorial" width="430" height="254"></a>
    <a href="http://www.bradoncode.com/tutorials/angularjs-unit-testing/" title="AngularJS Testing - Unit Testing Tutorials"><img src="http://www.bradoncode.com/assets/img/ngmock-testing.png" alt="AngularJS Testing - Unit Testing Tutorials" width="430" height="254"></a>
  </div>
    
  
  </section>
