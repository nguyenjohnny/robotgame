import tkinter


class Robot(object):
    """
    Arguments:
    name (string): robot's name
    color (string): robot's color
    row (int) : position of robot on x-intercept
    column (int): position of robot on y-intercept

    Attributes:
    name (string): name of robot
    color (string): color of robot
    row (int) : position of robot on x-intercept
    column (int): position of robot on y-intercept
    battery (int): shows the current battery of the robot, defaults at 0
    """

    # class variable used by the show method
    unit_size = 60

    # Class variable describing the maze
    # False represents an obstacle, True represents open space
    maze = [[True, True, False, True, True, True, False, True, True, True],
            [True, True, False, True, True, True, False, True, True, True],
            [True, False, True, True, True, True, False, True, True, True],
            [True, True, True, True, True, True, True, True, False, True],
            [True, True, True, True, True, True, True, True, False, True],
            [True, True, True, True, True, True, True, True, True, True],
            [True, False, False, False, False, True, True, True, True, True],
            [True, True, False, True, True, True, True, True, False, True],
            [True, False, True, True, True, True, True, True, False, True],
            [True, True, True, True, True, True, True, True, False, True]]

    maze_size = len(maze)
    # class variable to represent the maximum charge
    # A robot with a fully charged battery can take up to 20 steps
    max_charge = 20

    def __init__(self,  name, color, row=0, column=0):
        self.name = name
        self.color = color
        self.row = row
        self.column = column
        self.battery = 0

    def __str__(self):
        return '{} is a {} robot, exploring the maze.'.format(self.name,self.color)

    def __le__(self, other):
        """
        A magic method that checks if the self object has less battery than another object

        :param other:
        :return: self less than other
        """
        return self.battery <= other.battery

    def recharge(self):
        """
        recharges the robot to the maximum battery

        :param: None
        :return: self
        """
        if self.battery == 0:
            self.battery = self.max_charge
            return self

    def one_step_forward(self):
        """
        Takes the robot one step forward, if there is an obstacle, then the robot's battery becomes 0
        and the robot is moved back to (0,0). If the robot attempts to move outside the maze, then
        it will prompt that the robot is out of bound.

        :param: None
        :return: self
        """
        if self.battery > 0:
            if self.row+1 >= self.maze_size:
                print('You are out of bound, please try again')
            elif self.maze[self.row+1][self.column] == False:
                print('You have lost, please try again')
                self.battery = 0
                self.row,self.column = 0,0
            else:
                self.row += 1
                self.battery -=1
        else:
            print('Please recharge the battery before starting')
            return self

    def one_step_back(self):
        """
        Takes the robot one step back, if there is an obstacle, then the robot's battery becomes 0
        and the robot is moved back to (0,0). If the robot attempts to move outside the maze, then
        it will prompt that the robot is out of bound.

        :param: None
        :return: self
        """
        if self.battery > 0:
            if self.row-1 <= 0 or self.row < 0:
                print('You are out of bound, please try again')
            elif self.maze[self.row-1][self.column] == False:
                print('You have lost, please try again')
                self.battery = 0
                self.row,self.column = 0,0
            else:
                self.row -= 1
                self.battery -= 1
        else:
            print('Please recharge the battery before starting')
            return self

    def one_step_right(self):
        """
        Takes the robot one step right, if there is an obstacle, then the robot's battery becomes 0
        and the robot is moved back to (0,0). If the robot attempts to move outside the maze, then
        it will prompt that the robot is out of bound.

        :param: None
        :return: self
        """
        if self.battery > 0:
            if self.column + 1 >= self.maze_size:
                print('You are out of bound, please try again')
            elif  self.maze[self.row][self.column + 1] == False:
                print('You have lost, please try again')
                self.battery = 0
                self.row,self.column = 0,0
            else:
                self.column += 1
                self.battery -= 1
        else:
            print('You do not have enough battery, please recharge to continue.')
            return self

    def one_step_left(self):
        """
        Takes the robot one step left, if there is an obstacle, then the robot's battery becomes 0
        and the robot is moved back to (0,0). If the robot attempts to move outside the maze, then
        it will prompt that the robot is out of bound.

        :param: None
        :return: self
        """
        if self.battery > 0:
            if self.column - 1 <= self.maze_size:
                print('You are out of bound, please try again')
            elif self.maze[self.row][self.column - 1] == False:
                print('You have lost, please try again')
                self.battery = 0
                self.row,self.column = 0,0
            else:
                self.column -=1
                self.battery -= 1
        else:
            print('You do not have enough battery, please recharge to continue.')
            return self

    def forward(self, steps):
        """
        Takes the robot one step forward a certain desired of steps, if there is an obstacle, then the robot's battery becomes 0
        and the robot is moved back to (0,0). If the robot attempts to move outside the maze, then
        it will prompt that the robot is out of bound.

        :param: None
        :return: self
        """
        if self.battery >= steps:
            if self.row + steps >= self.maze_size:
                print('You are out of bound, please try again')
            else:
                for step in range(steps):
                        self.one_step_forward()
        else:
            print('You do not have enough battery, please recharge to continue.')
            return self

    def backward(self, steps):
        """
        Takes the robot one step backwards a desired amount of steps, if there is an obstacle, then the robot's battery becomes 0
        and the robot is moved back to (0,0). If the robot attempts to move outside the maze, then
        it will prompt that the robot is out of bound.

        :param: None
        :return: self
        """
        if self.battery > steps:
            if self.row + steps <= self.maze_size:
                print('You are out of bound, please try again')
            else:
                for step in range(steps):
                    self.one_step_back()
        else:
            print('You do not have enough battery, please recharge to continue.')
            return self

    def right(self, steps):
        """
        Takes the robot one right backwards a desired amount of steps, if there is an obstacle, then the robot's battery becomes 0
        and the robot is moved back to (0,0). If the robot attempts to move outside the maze, then
        it will prompt that the robot is out of bound.

        :param: None
        :return: self
        """
        if self.battery > steps:
            if self.column + steps >= self.maze_size:
                print('You are out of bound, please try again')
            else:
                for step in range(steps):
                    self.one_step_right()
        else:
            print('You do not have enough battery, please recharge to continue')
            return self

    def left(self, steps):
        """
        Takes the robot one step left a desired amount of steps, if there is an obstacle, then the robot's battery becomes 0
        and the robot is moved back to (0,0). If the robot attempts to move outside the maze, then
        it will prompt that the robot is out of bound.

        :param: None
        :return: self
        """
        if self.battery > steps:
            if self.column + steps <= self.maze_size:
                print('You are out of bound, please try again')
            else:
                for step in range(steps):
                    self.one_step_left()
        else:
            print('You do not have enough battery, please recharge to continue')
            return self

    def show(self):
        """
        Draw a graphical representation of the robot in the maze.

        Parameter: None
        Return: None
        """
        root = tkinter.Tk()
        root.title(self.name + ' in the Maze')
        canvas = tkinter.Canvas(root, background='light green',
                                width=self.unit_size * self.maze_size,
                                height=self.unit_size * self.maze_size)
        canvas.grid()

        # draw a representation of the robot in the maze
        if self.battery:
            upper_x = self.column * self.unit_size + self.unit_size / 4
            upper_y = self.row * self.unit_size
            lower_x = upper_x + self.unit_size / 2
            lower_y = upper_y + self.unit_size
            eye_x = lower_x - 3 * self.unit_size / 20
            eye_y = upper_y + self.unit_size / 10

        else: # the robot ran out of battery
            upper_x = self.column * self.unit_size
            upper_y = self.row * self.unit_size + self.unit_size / 2
            lower_x = upper_x + self.unit_size
            lower_y = upper_y + self.unit_size / 2
            eye_x = lower_x - 9 * self.unit_size / 10
            eye_y = lower_y - 3 * self.unit_size / 20

        rectangle = canvas.create_rectangle(upper_x,
                                            upper_y,
                                            lower_x,
                                            lower_y,
                                            fill=self.color)
        # draw the robot's eyes
        canvas.create_oval(upper_x + self.unit_size / 10,
                           upper_y + self.unit_size / 10,
                           upper_x + 3 * self.unit_size / 20,
                           upper_y + 3 * self.unit_size / 20,
                           fill='black')
        canvas.create_oval(eye_x,
                           eye_y,
                           eye_x + self.unit_size / 20,
                           eye_y + self.unit_size / 20,
                           fill='black')
        # draw the obstacles in the maze
        for row in range(self.maze_size):
            for col in range(self.maze_size):
                if not self.maze[row][col]:
                    canvas.create_rectangle(col * self.unit_size,
                                            row * self.unit_size,
                                            (col + 1) * self.unit_size,
                                            (row + 1) * self.unit_size,
                                            fill='red')
        for row in range(self.maze_size):
            canvas.create_line(0,
                               row * self.unit_size,
                               self.maze_size * self.unit_size,
                               row * self.unit_size)
        for col in range(self.maze_size):
            canvas.create_line(col * self.unit_size,
                               0,
                               col * self.unit_size,
                               self.maze_size * self.unit_size)
        root.mainloop()

class UnderWaterRobot(Robot):

    max_charge = 30

    def __init__(self,name,color,depth,row=0,column=0):
        self.depth = depth
        super(UnderWaterRobot,self).__init__(name,color,row,column)
    def __str__(self):
        return f'{self.name} is a s {self.color} robot diving under water'

    def recharge(self):
        super(UnderWaterRobot,self).recharge()

    def one_step_forward(self):
        super(UnderWaterRobot, self).one_step_forward()

    def one_step_back(self):
        super(UnderWaterRobot, self).one_step_back()

    def one_step_left(self):
        super(UnderWaterRobot, self).one_step_left()

    def one_step_right(self):
        super(UnderWaterRobot, self).one_step_right()

    def forward(self, steps):
        super(UnderWaterRobot, self).forward(steps)

    def backward(self, steps):
        super(UnderWaterRobot, self).backward(steps)

    def right(self, steps):
        super(UnderWaterRobot, self).right(steps)

    def left(self, steps):
        super(UnderWaterRobot, self).left(steps)

    def dive(self,distance):
        """
        Adds a given distance to the underwater depth (modifies depth)

        :param distance (int): a distance integer
        :return: depth
        """
        self.depth = distance
        return self.depth
