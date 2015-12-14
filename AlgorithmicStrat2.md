
Consider the following program which is an example of Strategy Design pattern Implemented in C++:
Strategy is the base class based on which the application class TestBed is developed. The base class provides us with an <i>Algorithmic</i> template to develope the application class.

<pre><code>
class Strategy;

class TestBed
{
  public:
    enum StrategyType
    {
        Dummy, Left, Right, Center
    };
    TestBed()
    {
        strategy_ = NULL;
    }
    void setStrategy(int type, int width);
    void doIt();
  private:
    Strategy *strategy_;
};

class Strategy
{
  public:
    Strategy(int width): width_(width){}
    void format()
    {
        char line[80], word[30];
        ifstream inFile("quote.txt", ios::in);
        line[0] = '\0';

        inFile >> word;
        strcat(line, word);
        while (inFile >> word)
        {
            if (strlen(line) + strlen(word) + 1 > width_)
              justify(line);
            else
              strcat(line, " ");
            strcat(line, word);
        }
        justify(line);
    }
  protected:
    int width_;
  private:
    virtual void justify(char *line) = 0;
};

class LeftStrategy: public Strategy
{
  public:
    LeftStrategy(int width): Strategy(width){}
  private:
     /* virtual */void justify(char *line)
    {
        cout << line << endl;
        line[0] = '\0';
    }
};

class RightStrategy: public Strategy
{
  public:
    RightStrategy(int width): Strategy(width){}
  private:
     /* virtual */void justify(char *line)
    {
        char buf[80];
        int offset = width_ - strlen(line);
        memset(buf, ' ', 80);
        strcpy(&(buf[offset]), line);
        cout << buf << endl;
        line[0] = '\0';
    }
};

class CenterStrategy: public Strategy
{
  public:
    CenterStrategy(int width): Strategy(width){}
  private:
     /* virtual */void justify(char *line)
    {
        char buf[80];
        int offset = (width_ - strlen(line)) / 2;
        memset(buf, ' ', 80);
        strcpy(&(buf[offset]), line);
        cout << buf << endl;
        line[0] = '\0';
    }
};

void TestBed::setStrategy(int type, int width)
{
  delete strategy_;
  if (type == Left)
    strategy_ = new LeftStrategy(width);
  else if (type == Right)
    strategy_ = new RightStrategy(width);
  else if (type == Center)
    strategy_ = new CenterStrategy(width);
}

void TestBed::doIt()
{
  strategy_->format();
}

int main()
{
  TestBed test;
  int answer, width;
  cout << "Exit(0) Left(1) Right(2) Center(3): ";
  cin >> answer;
  while (answer)
  {
    cout << "Width: ";
    cin >> width;
    test.setStrategy(answer, width);
    test.doIt();
    cout << "Exit(0) Left(1) Right(2) Center(3): ";
    cin >> answer;
  }
  return 0;
}
</code></pre>

The output of the above program is as follows:
<pre><code>
Exit(0) Left(1) Right(2) Center(3): 2
Width: 75
Exit(0) Left(1) Right(2) Center(3): 3
Width: 75
</code></pre>


[<img src="https://cloud.githubusercontent.com/assets/14101008/11768481/3b7d20d6-a18b-11e5-95fe-a422966f4c03.png" width="50" height="50"></img>](https://github.com/hariniiyer/CSCI-5828_Presentation4_Software-Design-Patterns/blob/master/AlgorithmicStrat.md)
[<img src="https://encrypted-tbn1.gstatic.com/images?q=tbn:ANd9GcQDyx6SDBF0wYKX7oVbtC-3-mmhmX0T0S1neRIapHQG9-7yWrw7" width="50" height="50"></img>](https://github.com/hariniiyer/CSCI-5828_Presentation4_Software-Design-Patterns/blob/master/CompDesign.md)
